<?php
ob_start();
session_start();

$pageTitle = "Notícias";

/* =========================
   CONFIGURAÇÕES
========================= */
const FICHEIRO = "noticias.json";
const PASTA_UPLOADS = "uploads_noticias/";

if (!is_dir(PASTA_UPLOADS)) {
    mkdir(PASTA_UPLOADS, 0777, true);
}

if (!file_exists(FICHEIRO)) {
    file_put_contents(FICHEIRO, json_encode([], JSON_PRETTY_PRINT));
}

$noticias = json_decode(file_get_contents(FICHEIRO), true) ?: [];

/* =========================
   APAGAR NOTÍCIA
========================= */
if (
    isset($_GET['apagar']) &&
    isset($_SESSION['perfil']) &&
    $_SESSION['perfil'] === 'admin'
) {
    $id = (int) $_GET['apagar'];

    if (isset($noticias[$id])) {

        if (
            !empty($noticias[$id]['imagem']) &&
            file_exists($noticias[$id]['imagem']) &&
            $noticias[$id]['imagem'] !== 'img/default.jpg'
        ) {
            unlink($noticias[$id]['imagem']);
        }

        unset($noticias[$id]);

        $noticias = array_values($noticias);

        file_put_contents(
            FICHEIRO,
            json_encode($noticias, JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE)
        );

        header("Location: noticias.php");
        exit;
    }
}

/* =========================
   ADICIONAR NOTÍCIA
========================= */
if (
    isset($_POST['adicionar']) &&
    isset($_SESSION['perfil']) &&
    in_array($_SESSION['perfil'], ['admin', 'editor'])
) {

    $titulo = trim($_POST['titulo'] ?? '');
    $descricao = trim($_POST['descricao'] ?? '');
    $texto = trim($_POST['texto'] ?? '');

    $imagem = "img/default.jpg";
    $data = date("d/m/Y");

    if (!empty($_FILES['imagem']['name'])) {

        $extensao = strtolower(
            pathinfo($_FILES['imagem']['name'], PATHINFO_EXTENSION)
        );

        $permitidas = ['jpg', 'jpeg', 'png', 'gif', 'webp'];

        if (in_array($extensao, $permitidas)) {

            $nomeFicheiro = time() . "_" .
                preg_replace(
                    '/[^a-zA-Z0-9._-]/',
                    '',
                    $_FILES['imagem']['name']
                );

            $destino = PASTA_UPLOADS . $nomeFicheiro;

            if (
                move_uploaded_file(
                    $_FILES['imagem']['tmp_name'],
                    $destino
                )
            ) {
                $imagem = $destino;
            }
        }
    }

    $noticias[] = [
        "titulo"     => $titulo,
        "data"       => $data,
        "imagem"     => $imagem,
        "descricao"  => $descricao,
        "texto"      => $texto
    ];

    file_put_contents(
        FICHEIRO,
        json_encode($noticias, JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE)
    );

    header("Location: noticias.php");
    exit;
}

include 'includes/header.php';
include 'includes/menu.php';
?>

<section class="noticias">
    <div class="container">

        <h1>Últimas Notícias</h1>

        <?php if (
            isset($_SESSION['perfil']) &&
            in_array($_SESSION['perfil'], ['admin', 'editor'])
        ): ?>

            <div class="form">
                <form method="POST" enctype="multipart/form-data">

                    <input
                        type="text"
                        name="titulo"
                        placeholder="Título"
                        required
                    >

                    <input
                        type="text"
                        name="descricao"
                        placeholder="Descrição"
                        required
                    >

                    <textarea
                        name="texto"
                        placeholder="Texto completo"
                        required
                    ></textarea>

                    <input type="file" name="imagem">

                    <button type="submit" name="adicionar">
                        Adicionar Notícia
                    </button>

                </form>
            </div>

        <?php endif; ?>

        <div class="grid">

            <?php foreach ($noticias as $id => $n): ?>

                <div class="card">

                    <img
                        src="<?= htmlspecialchars($n['imagem']) ?>"
                        alt="<?= htmlspecialchars($n['titulo']) ?>"
                    >

                    <div class="conteudo">

                        <span><?= htmlspecialchars($n['data']) ?></span>

                        <h2>
                            <?= htmlspecialchars($n['titulo']) ?>
                        </h2>

                        <p>
                            <?= htmlspecialchars($n['descricao']) ?>
                        </p>

                        <button onclick="abrirModal(<?= $id ?>)">
                            Ler Mais
                        </button>

                        <?php if (
                            isset($_SESSION['perfil']) &&
                            $_SESSION['perfil'] === 'admin'
                        ): ?>
                            <br><br>

                            <a
                                href="?apagar=<?= $id ?>"
                                onclick="return confirm('Apagar notícia?')"
                            >
                                🗑 Apagar
                            </a>
                        <?php endif; ?>

                    </div>

                </div>

            <?php endforeach; ?>

        </div>

    </div>
</section>

<!-- MODAL -->
<div id="modal" class="modal">

    <div class="modal-content">

        <span class="fechar" onclick="fecharModal()">
            &times;
        </span>

        <img id="m_img" alt="" style="width:100%;margin-bottom:15px;">

        <h2 id="m_titulo"></h2>

        <span id="m_data"></span>

        <p id="m_texto"></p>

    </div>

</div>

<script>
const noticias = <?= json_encode(
    $noticias,
    JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_SLASHES
); ?>;

function abrirModal(id) {

    document.getElementById("m_img").src =
        noticias[id].imagem;

    document.getElementById("m_titulo").innerText =
        noticias[id].titulo;

    document.getElementById("m_data").innerText =
        noticias[id].data;

    document.getElementById("m_texto").innerText =
        noticias[id].texto;

    document.getElementById("modal").style.display = "flex";
}

function fecharModal() {
    document.getElementById("modal").style.display = "none";
}

window.onclick = function(e) {
    const modal = document.getElementById("modal");

    if (e.target === modal) {
        fecharModal();
    }
};
</script>

<style>
body{
    margin:0;
    font-family:Arial, sans-serif;
    background:#f5f5f5;
}

.container{
    max-width:1200px;
    margin:auto;
    padding:20px;
}

h1{
    text-align:center;
    margin-bottom:30px;
}

.form{
    margin-bottom:50px;
}

.form form{
    display:flex;
    flex-direction:column;
    gap:12px;
    max-width:600px;
    margin:auto;
}

.form input,
.form textarea{
    padding:12px;
    border:1px solid #ccc;
    border-radius:8px;
}

.form textarea{
    min-height:150px;
    resize:vertical;
}

button{
    padding:12px;
    border:none;
    border-radius:8px;
    background:#007bff;
    color:#fff;
    cursor:pointer;
}

button:hover{
    opacity:.9;
}

.grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(300px,1fr));
    gap:30px;
}

.card{
    background:#fff;
    border-radius:12px;
    overflow:hidden;
    box-shadow:0 4px 12px rgba(0,0,0,.1);
}

.card img{
    width:100%;
    height:220px;
    object-fit:cover;
}

.conteudo{
    padding:15px;
}

.modal{
    display:none;
    position:fixed;
    inset:0;
    background:rgba(0,0,0,.7);
    justify-content:center;
    align-items:center;
    z-index:9999;
}

.modal-content{
    background:#fff;
    width:90%;
    max-width:700px;
    max-height:90vh;
    overflow-y:auto;
    border-radius:10px;
    padding:20px;
    position:relative;
}

.fechar{
    position:absolute;
    right:15px;
    top:10px;
    font-size:30px;
    cursor:pointer;
}
</style>

<?php
include 'includes/footer.php';
ob_end_flush();
?>
