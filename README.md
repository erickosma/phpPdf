Inntrodução 
===================



Projeto com exemplo de manipulação de **PDF** com **PHP**.
Extração de texto de PDF e imagens 
1. Extrair texto de um PDF
2. Extrair imagem de um PDF
3. Extrair texto de uma imagem 

#Requerimentos
 * PHP 5.6
 



# Extrair texto de arquivo  pdf 

## Install

Adicionar o  PDFParser no seu arquivo  composer.json  :


```json
    {
        "require": {
            "smalot/pdfparser": "^0.10.0"
        }
    }
 ```

Ou no terminal executar o comando 
```bash
 $ composer require smalot/pdfparser
```

O comando vai fazer o download de todas as dependências e ira criar o ```autoload.php``` 


## Uso 
Agora, crie um novo arquivo com esse conteúdo:
Esta amostra irá analisar todo o arquivo pdf e extrair texto de cada página.

```  /src/exemplos/extracttextpdf.php  ```


```php
// Include Composer autoloader if not already done.
include 'vendor/autoload.php';
 
// Parse pdf file and build necessary objects.
$parser = new \Smalot\PdfParser\Parser();
$pdf    = $parser->parseFile('document.pdf');
 
$text = $pdf->getText();
echo $text;
```

Podemos extrair também documentos por página


```php
// Include Composer autoloader if not already done.
include 'vendor/autoload.php';
 
// Parse pdf file and build necessary objects.
$parser = new \Smalot\PdfParser\Parser();
$pdf    = $parser->parseFile('document.pdf');
 
// Retrieve all pages from the pdf file.
$pages  = $pdf->getPages();

// Loop over each page to extract text.
foreach ($pages as $page) {
 echo $page->getText();
}
 
```

