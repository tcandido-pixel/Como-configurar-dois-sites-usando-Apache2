# Como-configurar-dois-sites-usando-Apache2

Este guia mostra como configurar dois sites diferentes no mesmo servidor Apache2, utilizando Virtual Hosts.

----

* 📌 1. Criar diretórios para os sites

No diretório /var/www, crie as pastas dos sites:

* ```cd /var/www```

* ```sudo mkdir -p site1/public_html```

* ```sudo mkdir -p site2/public_html```
----

Dê permissão ao seu usuário para editar os arquivos:

* ```sudo chown -R $USER:$USER /var/www/site1/public_html```

* ```sudo chown -R $USER:$USER /var/www/site2/public_html```
----

* 📌2. Criar páginas de exemplo

Site1

* ```cd /var/www/site1/public_html```
  
* ```sudo nano index.html```

* Exemplo de conteúdo:

   
