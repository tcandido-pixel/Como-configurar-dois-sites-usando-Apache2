# Como-configurar-dois-sites-usando-Apache2

Este guia mostra como configurar dois sites diferentes no mesmo servidor Apache2, utilizando Virtual Hosts.

----

* 📌 1. Criar diretórios para os sites

No diretório /var/www, crie as pastas dos sites:

* ```cd /var/www```

* ```sudo mkdir -p site1/public_html```

* ```sudo mkdir -p site2/public_html```

Dê permissão ao seu usuário para editar os arquivos:

* ```sudo chown -R $USER:$USER /var/www/site1/public_html```

* ```sudo chown -R $USER:$USER /var/www/site2/public_html```
----

* 📌2. Criar páginas de exemplo

Site1

* ```cd /var/www/site1/public_html```
  
* ```sudo nano index.html```

Exemplo de conteúdo:
```
<html>
<head>
<title>Página do Site 1</title>
</head>
<body>
<h1>Site 1</h1>
</body>
</html>
```
Site2 

* ```cd /var/www/site2/public_html```
  
* ```sudo nano index.html```

Exemplo de conteúdo:
```
<html>
<head>
<title>Página do Site 2</title>
</head>
<body>
<h1>Site 2</h1>
</body>
</html>
```
-----

* 📌 3. Criar arquivos de configuração no Apache2

Entre no diretório de configuração:

* ```cd /etc/apache2/sites-available/```
  
Copie o arquivo padrão para criar o do site1:

* ```sudo cp 000-default.conf site1.conf```
  
Edite o site1.conf:

* ```sudo nano site1.conf```
  
Coloque algo assim:
```
ServerAdmin admin@site1
ServerName site1
ServerAlias www.site1
DocumentRoot /var/www/site2/public_html
```
Agora crie o do site2:

* ```sudo cp site1.conf site2.conf```
  
* ```sudo nano site2.conf```

Edite para:
```
ServerAdmin admin@site2
ServerName site2
ServerAlias www.site2
DocumentRoot /var/www/site2/public_html
```
-----

* 📌 4. Ativar os sites no Apache

Edite o arquivo para mapear os nomes para localhost:

* ```sudo nano /etc/hosts```

Adicione no final:

* ```127.0.0.1 site1.local```

* ```127.0.0.1 site2.local```

-----

* 📌 6. Testar no navegador
  
Abra o navegador e acesse:

* ```http://site1/ → deve mostrar a página do Site 1```

* ```http://site2/ → deve mostrar a página do Site 2```

-----

* 🎉 Conclusão

Agora você tem dois sites diferentes rodando no mesmo servidor Apache2, cada um com seu diretório e configuração própria.
