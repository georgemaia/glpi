# GLPI

[![GLPI Screen Shot][product-screenshot]](https://glpi-project.org)

Procedimentos aplicados durante instalação do GLPI

## Configuração para Desenvolvimento

### **Instalação pré-requisitos obrigatórios Ubuntu 14.04**

[https://glpi-install.readthedocs.io/en/latest/prerequisites.html](https://glpi-install.readthedocs.io/en/latest/prerequisites.html)

```bash
apt-get install apache2 php php-curl php-gd php-cli php-mbstring php-mysql php-xml -y  
apt-get install mariadb-server -y
```

### **Instalar pré-requisitos opcionais**

```bash
apt-get install php-cli php-cas php-imap php-ldap php-xmlrpc php-soap php-snmp php-apcu -y
```

### **Instalar utilitários**

```bash
apt-get install zip unzip bzip2 unrar-free vim -y
```

### **Ajustes no php.ini**

```ini
memory_limit = 64M ; // max memory limit  
file_uploads = on ;  
max_execution_time = 600 ; // not mandatory but adviced  
register_globals = off ; // not mandatory but adviced  
magic_quotes_sybase = off ;  
session.auto_start = off ;  
session.use_trans_sid = 0 ; // not mandatory but adviced

```

### **Download GLPI**

```bash
cd /tmp  
wget https://github.com/glpi-project/glpi/releases/download/9.4.3/glpi-9.4.3.tgz 
tar -xvzf glpi-9.4.3.tgz  
cp -Rf glpi /var/www/html

```

### **Permissões para a pasta do GLPI**

```bash
chmod 775 /var/www/html/* -Rf
chown www-data. /var/www/html/* -Rf
chmod 777 /var/www/html/glpi/files
chmod 777 /var/www/html/glpi/config
chmod 777 /var/www/html/glpi/files/_dumps
chmod 777 /var/www/html/glpi/files/_sessions
chmod 777 /var/www/html/glpi/files/_cron
chmod 777 /var/www/html/glpi/files/_cache
chmod 777 /var/www/html/glpi/files/_log
chmod 777 /var/www/html/glpi/files/_lock
chmod 777 /var/www/html/glpi/files/_graphs
chmod 777 /var/www/html/glpi/files/_pictures
chmod 777 /var/www/html/glpi/files/_rss
chmod 777 /var/www/html/glpi/files/_tmp
chmod 777 /var/www/html/glpi/files/_uploads
chmod 777 /var/www/html/glpi/files/_plugins
```

### **Criação do banco de dados do GLPI**

```bash
mysql -uroot -p  

mysql> create database glpi;

mysql> create user 'glpi'@'localhost' identified by '123456';

mysql> grant all on glpi.* to glpi identified by '123456';

mysql> quit;

```

### **Configuração de segurança de diretórios do GLPi**

 vim /etc/apache2/conf-available/glpi.conf

        a2enconf glpi.conf
    
        service apache2 restart

### Migração de tabelas para InnoDB

[http://www.thiagopassamani.com.br/glpi/tabelas-nao-migradas-para-o-mecanismo-innodb.html](http://www.thiagopassamani.com.br/glpi/tabelas-nao-migradas-para-o-mecanismo-innodb.html)

### Alterar valores padrão

Configurar - geral - valores padrão

Alterar formato de nome, número


### Abertura por email

[![GLPI Email](https://img.youtube.com/vi/toiG6f6TETU/0.jpg)](https://www.youtube.com/watch?v=toiG6f6TETU&feature=emb_logo)

[Videos do Youtube sobre notificação e abertura por email](https://www.youtube.com/results?search_query=glpi+destinat%C3%A1rio+email)

---

## Contributing

1. Faça o _fork_ do projeto (<https://github.com/yourname/yourproject/fork>)
2. Crie uma _branch_ para sua modificação (`git checkout -b feature/fooBar`)
3. Faça o _commit_ (`git commit -am 'Add some fooBar'`)
4. _Push_ (`git push origin feature/fooBar`)
5. Crie um novo _Pull Request_

---

## Referências

[OLIVEIRA, Daniel de. **Estudo de caso para a implantação de uma ferramenta de Service Desk no NRC/UFJF**. 2017. 115 f. TCC (Graduação) - Curso de Sistemas de Informação, Ciências da Computação, Universidade Federal de Juiz de Fora, Juiz de Fora/MG, 2017.](docs/TCC_danieldeoliveira.pdf)

[PERONDI, Leandro Teixeira. **Sistema para gerenciamento de chamados técnicos**. 2013. 91 f. TCC (Graduação) - Curso de Bacharel em Sistemas de Informação, Centro de Computação e Tecnologia da Informação, Universidade de Caxias do Sul, Caxias do Sul/RS, 2013.](docs/TCC_leandroteixeiraperondi.pdf)

[LOPES, Santiago José Franco. **Melhoria dos serviços de TI utilizando o gerenciamento de serviços**. 2016. 106 f. Dissertação (Mestrado Profissional) - Curso de Engenharia de Produção, Universidade Estadual Paulista "júlio de Mesquita Filho", Guaratinguetá/SP, 2016](docs/TCC_santianojosefrancolopes.pdf)

[Catalogo de Serviços Computel](docs/Catalogo_de_Servicos_Computel.pdf)

[Catálogo de Serviços HU-UFJF](docs/Catalogo_Servicos_HU-UFJF.pdf)

[Apresentação Gestão de Ativos - George Maia](docs/Gestao_de_ativos_georgemaia.pdf)

[Apresentação Instalação GLPI no Debian 9 - Halexsandro de Freitas Sales](https://pt.slideshare.net/halexsandro/glpi-debian-9)

[https://www.arthurschaefer.com.br/2019/01/29-instalando-o-glpi-9-3-3-no-debian-9/](https://www.arthurschaefer.com.br/2019/01/29-instalando-o-glpi-9-3-3-no-debian-9/)

[http://www.thiagopassamani.com.br/glpi/abertura-de-chamados-no-glpi-via-e-mail.html](http://www.thiagopassamani.com.br/glpi/abertura-de-chamados-no-glpi-via-e-mail.html)

<!-- MARKDOWN LINKS & IMAGES -->
[product-screenshot]: img/screenshot.png