<?php 
$pageTitle = "Prestação de Contas";
include 'includes/header.php'; 
include 'includes/menu.php'; 

/* =========================
   TEUS DOCUMENTOS FIXOS (NÃO MEXIDO)
========================= */
$documentos = [

 "2025" => [
        [
            "titulo" => "Relatório de Atividades 2025",
            "link" => "img/Relatorio-de-Gestao-do-exercicio-2025-ORIG.pdf"
        ],
        [
            "titulo" => "Relatório de Gestão do exercício 2025",
            "link" => "img/Relatorio-de-Gestao-do-exercicio-2025-Comprimido.pdf"
        ],
        [
            "titulo" => "Acta do Conselho Fiscal 2025",
            "link" => "img/Ata-do-CF2025.pdf"
        ],
        [
            "titulo" => "Parecer do Conselho Fiscal 2025",
            "link" => "img/Parecer-CF2025.pdf"
        ],
        [
            "titulo" => "Declaração Responsabilidade 2025",
            "link" => "img/Declaracao-de-responsabilidade2025.pdf"
        ]
    ],

    "2024" => [
        [
            "titulo" => "Relatório de contas 2024",
            "link" => "img/RelatoriodeContas2024-compactado-1.pdf"
        ],
        [
            "titulo" => "Ata Conselho Fiscal contas 2024",
            "link" => "img/ActaDireccaoContas2024.pdf"
        ],
        [
            "titulo" => "Parecer Conselho Fiscal Contas 2024",
            "link" => "img/Parecer-CFcontas2024.pdf"
        ],
        [
            "titulo" => "Ata Aprovação de Contas 2024",
            "link" => "img/ActaDireccaoContas2024.pdf"
        ]
    ],

    "2023" => [
        [
            "titulo" => "Relatório de contas 2023",
            "link" => "img/Relatorio-de-Contas-2023_compressed-1-2.pdf"
        ],
        [
            "titulo" => "Parecer do Conselho Fiscal 2023",
            "link" => "img/Parecer-do-Conselho-Fiscal2023.pdf"
        ],
        [
            "titulo" => "Declaração Responsabilidade 2023",
            "link" => "img/Declaracao-de-responsabilidade-Contas-2023-1.pdf"
        ],
        [
            "titulo" => "Ata Aprovação de Contas 2023",
            "link" => "img/Acta-de-aprovacao-de-contas-2023-1.pdf"
        ]
    ],

    "2022" => [
        [
            "titulo" => "Relatório de contas 2022",
            "link" => "img/Relatorio-de-contas-2022_compressed-1.pdf"
        ],
        [
            "titulo" => "Ata Conselho Fiscal contas 2022",
            "link" => "img/Ata-Conselho-Fiscal-Contas-2022.pdf"
        ],
        [
            "titulo" => "Parecer Conselho Fiscal Contas 2022",
            "link" => "img/Parecer-Conselho-Fiscal-Contas-2022.pdf"
        ],
        [
            "titulo" => "Ata Aprovação de Contas 2022",
            "link" => "img/Acta-Aprovacao-de-Contas-2022.pdf"
        ],
        [
            "titulo" => "Declaração de Responsabilidade Final de Exercício 2022",
            "link" => "img/Declaracao-de-Responsabilidade-Final-de-Exercicio-2022.pdf"
        ]
    ],

    "2021" => [
        [
            "titulo" => "Relatório de Contas 2021",
            "link" => "img/Relatorio-de-contas-2021_compressed-1.pdf"
        ],
        [
            "titulo" => "Ata de Aprovação de Contas 2021",
            "link" => "img/Acta-de-Aprovacao-de-contas-2021.pdf"
        ],
        [
            "titulo" => "Ata Assembleia 2021",
            "link" => "img/Ata-Assembleia.pdf"
        ],
        [
            "titulo" => "Parecer do Conselho Fiscal 2021",
            "link" => "img/Parecer-do-Conselho-Fiscal.pdf"
        ],
        [
            "titulo" => "Declaração Responsabilidade 2021",
            "link" => "img/Declaracao-responsabilidade.pdf"
        ]
    ],

    "2020" => [
        [
            "titulo" => "Ata Assembleia 2020",
            "link" => "img/Ata-Assembleia 2020.pdf"
        ],
        [
            "titulo" => "Parecer do Conselho Fiscal 2020",
            "link" => "img/Parecer-do-Conselho-Fiscal 2020.pdf"
        ],
        [
            "titulo" => "Relatório de contas 2020",
            "link" => "img/Relatorio-e-contas 2020.pdf"
        ]
    ],

    "2019" => [
        [
            "titulo" => "Relatório de Contas 2019",
            "link" => "img/Relatório-de-Contas-2019_compressed-1.pdf"
        ],
        [
            "titulo" => "Ata de Aprovação de Contas Direcção 2019",
            "link" => "img/Acta-de-Aprovação-de-Contas-Direcção2019.pdf"
        ],
        [
            "titulo" => "Relatório de Actividades 2019",
            "link" => "img/Relatório-de-Actividades-2019.pdf"
        ]
    ],

    "2018" => [
        [
            "titulo" => "Relatório de Actividades 2018",
            "link" => "img/RelatórioActividades2018_compressed-1.pdf"
        ],
        [
            "titulo" => "Relatório de Contas 2018",
            "link" => "img/Relatório-de-Contas-2018_compressed.pdf"
        ],
        [
            "titulo" => "Declaração de responsabilidade 2018",
            "link" => "https://centroparoquial.almeirim.org/wp-content/uploads/2019/05/Declara%C3%A7%C3%A3o-responsabilidade2018-1.pdf"
        ]
    ],

    "2017" => [
        [
            "titulo" => "Relatório de Gestão de Contas de 2017",
            "link" => "img/Relatório-de-Gestão-de-Contas-de-2017-comprimido.pdf"
        ],
        [
            "titulo" => "Ata da Direcção Contas 2017",
            "link" => "img/ata-da-Direcção-Contas-2017-2.pdf"
        ],
        [
            "titulo" => "Ata do conselho fiscal contas 2017",
            "link" => "img/ata-do-conselho-fiscal-contas-2017-1.pdf"
        ],
        [
            "titulo" => "Parecer do Conselho Fiscal 2017",
            "link" => "img/relatórioatividades-2017-2.pdf"
        ],
        [
            "titulo" => "Relatório Atividades 2017",
            "link" => "documentos/2017/relatorio-atividades-2017.pdf"
        ],
        [
            "titulo" => "Orçamento 2018",
            "link" => "img/Orçamento-2018.pdf"
        ],
        [
            "titulo" => "Acta e Parecer do Conselho Fiscal 2017",
            "link" => "img/Acta-e-Parecer-do-Conselho-Fiscal-2017.pdf"
        ]
    ],

    "2016 / 2015" => [
        [
            "titulo" => "Relatório de Gestão e Exercício até 31 de Dezembro de 2016",
            "link" => "c:\Users\utilizador\Downloads\Relatório-de-Gestão-e-Exercício-até-31-de-Dezembro-de-2016-6.7z (1).zip"
        ],
        [
            "titulo" => "Relatório de actividades de 2016",
            "link" => "c:\Users\utilizador\Downloads\Relatório-de-actividades-de-2016.7z (1).zip"
        ],
        [
            "titulo" => "Ata de Aprovação da Direcção do Relatório do Exercício de 2016",
            "link" => "img/Acta-de-Aprovação-da-Direcção-do-Relatório-do-Exercício-de-2016.pdf"
        ],
        [
            "titulo" => "Relatório de Gestão do exercício até 31 de Dezembro de 2015",
            "link" => "img/Contas2015.pdf"
        ]
    ]

];


/* =========================
   UPLOAD DE NOVOS DOCUMENTOS
========================= */
$baseDir = "img/";

if(isset($_POST['upload'])){

    $ano = preg_replace('/[^0-9]/', '', $_POST['ano']);
    $titulo = trim($_POST['titulo']);

    $pasta = $baseDir . $ano . "/";

    if(!file_exists($pasta)){
        mkdir($pasta, 0777, true);
    }

    $fileName = basename($_FILES["ficheiro"]["name"]);
    $target = $pasta . $fileName;

    move_uploaded_file($_FILES["ficheiro"]["tmp_name"], $target);
}

/* =========================
   APAGAR NOVOS DOCUMENTOS
========================= */
if(isset($_GET['del'])){
    $file = $_GET['del'];
    if(file_exists($file)){
        unlink($file);
    }
}

/* =========================
   CARREGAR NOVOS DOCUMENTOS
========================= */
$pastas = glob($baseDir . "*", GLOB_ONLYDIR);

$novos = [];

foreach($pastas as $pasta){

    $ano = basename($pasta);

    $files = glob($pasta . "/*.pdf");

    foreach($files as $file){

        $novos[$ano][] = [
            "titulo" => basename($file, ".pdf"),
            "link" => $file
        ];
    }
}

/* =========================
   JUNTAR FIXOS + NOVOS
========================= */
foreach($novos as $ano => $lista){

    if(!isset($documentos[$ano])){
        $documentos[$ano] = [];
    }

    $documentos[$ano] = array_merge($documentos[$ano], $lista);
}

krsort($documentos);
?>

<section class="prestacao-contas">

<div class="container">

<h1>Prestação de Contas</h1>

<p class="subtitulo">Adicionar, ver e apagar documentos</p>

<!-- FORMULARIO -->
<div class="admin-box">

<form method="POST" enctype="multipart/form-data">

    <input type="text" name="ano" placeholder="Ano (ex: 2025)" required>
    <input type="text" name="titulo" placeholder="Título" required>
    <input type="file" name="ficheiro" required>

    <button type="submit" name="upload">Adicionar Documento</button>

</form>

</div>

<!-- DOCUMENTOS -->
<?php foreach($documentos as $ano => $lista): ?>

<div class="bloco-ano">

<h2><?= $ano; ?></h2>

<div class="grid-documentos">

<?php foreach($lista as $doc): ?>

<div class="card-documento">

<div class="icone">📄</div>

<h3><?= $doc['titulo']; ?></h3>

<a href="<?= $doc['link']; ?>" target="_blank" class="btn-download">
Ver Documento
</a>

<a href="?del=<?= $doc['link']; ?>" style="display:inline-block;margin-top:10px;padding:8px 12px;background:red;color:white;border-radius:6px;text-decoration:none;">
Apagar
</a>

</div>

<?php endforeach; ?>

</div>

</div>

<?php endforeach; ?>

</div>

</section>

<style>

.prestacao-contas{
    padding: 60px 20px;
    background: #f5f5f5;
}

.container{
    max-width: 1200px;
    margin: auto;
}

h1{
    text-align: center;
    font-size: 42px;
}

.subtitulo{
    text-align: center;
    margin-bottom: 30px;
}

.admin-box{
    background: white;
    padding: 20px;
    margin-bottom: 40px;
    border-radius: 10px;
}

.admin-box input{
    width: 100%;
    padding: 10px;
    margin: 5px 0;
}

.admin-box button{
    width: 100%;
    padding: 10px;
    background: green;
    color: white;
    border: none;
}

.bloco-ano h2{
    color: #007bff;
    border-left: 5px solid #007bff;
    padding-left: 10px;
}

.grid-documentos{
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px,1fr));
    gap: 20px;
}

.card-documento{
    background: white;
    padding: 20px;
    border-radius: 10px;
    text-align: center;
}

.btn-download{
    display: inline-block;
    margin-top: 10px;
    padding: 8px 12px;
    background: #007bff;
    color: white;
    text-decoration: none;
}

</style>

<?php include 'includes/footer.php'; ?>
