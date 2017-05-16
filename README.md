# Linux introdução

Esses são alguns comandos que vai te ajudar e com certeza ira precisar!
Esses comandos são apenas alguns dos milhares que temos , e é o necessário para começar a desbravar esse sistema incrível e não passar necessidades.

O que vamos ver hoje ? **Introdução ao comando Linux**

  - pwd
  - cd
  - mkdir
  - ls
  - touch
  - cat
  - tac
  - echo
  - head
  - tail
  - man
  - rmdir
  - rm
  - update-rc.d
  - clear

Conhecendo repositorios
  - apt-get
  - sources.list
  - Repositórios
  - Instalando programas
  - Removendo programas
  - Instalando arquivos .deb
  - Procurando programas

Criando um servidor LAMP
  - Instalando Apache2
  - Instalando Mysql Server
  - Instalando PHP5
  - Instalando biblioteca Mysql para o PHP

DeepWeb Servidor
  - Instalando TOR
  - Criando Hidden Service



## pwd
Mostra o local onde você está atualmente , esse comando é responsável por mostra-nos o caminho por inteiro da diretório em que nos encontramos em dado momento, ou seja um pathname.
```sh
pwd
```



## cd
O comando **cd** te leva a algum diretório , esse comando é responsável por mudar seu diretório atual.
```sh
cd
```

Podemos ver o diretório anterior com o
```sh
cd -
```



Ou podemos usar também o
```sh
cd $OLDPWD
```



## mkdir
O comando **mkdir** cria um **diretório/pasta** .
```sh
mkdir
```



## ls
O comando **ls** lista determinado **local/pasta** , esse comando é responsável por lista o conteúdo de uma diretório, semelhante ao comando dir no MS-DOS
```sh
ls
```

Já com o **ls -a** mostra todos os arquivos , até os ocultos
```sh
ls -a
ls -l
```

O ls é usado para listar determinado lugar , podemos ver um exemplo para listar um diretório
```sh
ls /
```

Podemos ver usado no diretório em que estamos
```sh
ls
```

Podemos também usar o formato de lista longa
```sh
ls -l
```

Para ver arquivos ocultos
```sh
ls -a
```



## touch
Cria um arquivo
```sh
touch
touch teste.txt
```

> Podemos também criar usando ** > **
```sh
   > nomedoarquivo
```



## cat
Mostra o conteúdo de um arquivo, como o comando type do MD-DOS, e é muito usado também para concatenar arquivos.
```sh
cat arquivo.txt
```

Como por exemplo fazendo
```sh
cat a.txt b.txt > c.txt
```

Para juntar o arquivo **a.txt** e **b.txt** num único de nome **c.txt**.



## tac
Ao contrario do **cat** o **tac** monstra o arquivo de forma **inversa**.
```sh
tac arquivo.txt
```



## echo
Imprime na tela/shell
```sh
echo
```

Adicionando nomes com o **>** , caso já tenha algum dado no arquivo será **sobrescrito**
```sh
echo "Júlio" > arquivo.txt
```

Adicionando nomes com o >> , nesse caso ele só é **adicionado** e não sobrescrito.
```sh
echo "Nome" >> arquivo.txt
```

Mais uma vez...
Sobrescreve
```sh
   echo teste > teste.txt  
```

Adiciona   
```sh
echo teste >> teste.txt
```

Vendo o antigo diretório podemos fazer  
```sh
echo $OLDPWD
```



## head
Mostra as primeiras linhas de um arquivo, como por exemplo com **head -10 a.txt**, ou usado como filtro para mostrar apenas os primeiros x resultados de outro comando.

Com o **head** é possível pegar o começo do arquivo , exemplo com o **-n 2** ele pega as duas primeiras linhas.

```sh
head
```

Mostra apenas as duas primeiras linhas do arquivo.
```sh
head -n 2
```



## tail
Funciona de forma inversa ao comando **head**, mostra-nos as últimas linhas de um arquivo ou mesmo do output de outro comando, quando usado como filtro.
```sh
tail
```

Com o comando **tail -n 2** ele mostra apenas as ultimas duas linhas do arquivo.
```sh
   tail -n 2
```

Com o comando **tail -f** você vê em tempo real o arquivo e caso foi adicionado algo exibi na hora.
```sh
tail -f arquivo.txt
```



## Man
Man vem de manual , exemplo.
```sh
man echo
man nmap
```



## rmdir
Ele é responsável por excluir pastas **vazias**.
```sh
rmdir
```



## rm
Apaga arquivo e não **diretório**.
```sh
rm
```

Já o **rm -rf** apaga arquivos e diretórios.
```sh
rm -rf
```

Nesse caso o **r** é de recursive , e o **f** de force.
Qualquer duvida faça **--help**
```sh
rm --help
```



## update-rc.d
**Update-rc.d** serve para adicionar e remover os script que serão inicializados no boot .

Vamos dar um exemplo **desabilitando** o serviço de ssh inicializado no **boot**.

**Desabilitando**
```sh
update-rc.d ssh disable
```

**Habilitando**
```sh
update-rc.d ssh enable
```



## clear
Limpar a tela
```sh
clear
```

ou o atalho
```sh
   Ctrl + l
```


## apt e apt-get
**APT** é um conjunto de ferramentas usadas pelo **GNU/Linux Debian** e suas respectivas derivações, entre eles o Ubuntu, para administrar os pacotes .deb de uma forma automática.

O apt-get é um interface simples de linha de comandos para obter e instalar pacotes.



## sources.list
Onde fica a sources.list ?
```sh
/etc/apt/sources.list
```


Como parte de sua operação, o **Apt** utiliza um arquivo que lista as 'fontes' das quais os pacotes podem ser obtidos. Este arquivo é **/etc/apt/sources.list**.

As entradas neste arquivo normalmente seguem este formato:

```sh
deb http://sítio.exemplo.com/debian distribuição componente1 componente2 componente3
deb-src http://sítio.exemplo.com/debian distribuição componente1 componente2 componente3
```

Obviamente, as entradas acima são fictícias e não devem ser usadas. A primeira palavra em cada linha, deb ou deb-src, indica o tipo de arquivo: se ele contem pacotes binários (deb), isto é, os pacotes pré-compilados que nós normalmente usamos, ou os pacotes-fonte (deb-src), que são os ?fontes originais do programa mais o arquivo de controle do Debian (.dsc) e o deff.gz contendo as alterações necessárias para o empacotamento do programa.

No meu caso é
```sh
#

# deb cdrom:[Debian GNU/Linux 8.5.0 _Jessie_ - Official amd64 NETINST Binary-1 $

#deb cdrom:[Debian GNU/Linux 8.5.0 _Jessie_ - Official amd64 NETINST Binary-1 2$

deb http://ftp.br.debian.org/debian/ jessie main
deb-src http://ftp.br.debian.org/debian/ jessie main

deb http://security.debian.org/ jessie/updates main
deb-src http://security.debian.org/ jessie/updates main

# jessie-updates, previously known as 'volatile'
deb http://ftp.br.debian.org/debian/ jessie-updates main
deb-src http://ftp.br.debian.org/debian/ jessie-updates main

#VirtualBox
deb http://download.virtualbox.org/virtualbox/debian jessie contrib


```

Estou usando um sistema Debian 8 (jessie) , dependendo de como você fez sua instalação podemos comentar (ou remover) as primeiras linhas que não referencia ao CD de instalação do Debian.

Após a modificação podemos atualizar nosso repositório.

Todos os pacotes incluídos na distribuição oficial do Debian são livres de acordo com a Definição Debian de Software Livre . Isso assegura o uso livre e a redistribuição de pacotes com seu código fonte completo. A distribuição oficial Debian é a que está contida na seção Main do repositório do Debian.


Como um serviço para os usuários do Debian são providos pacotes em seções separadas que não podem ser incluídas na distribuição main por causa de uma licença restritiva ou problemas legais. São eles:

**Contrib** Pacotes nessa área são livremente licenciados pelo detentor do copyright, mas dependem de outros pacotes que não são livres.


**Non-Free** (estes pacotes foram retirados do Debian a partir do Sarge) Pacotes nessa área apresentam algumas condições na licença que restringem o uso ou redistribuição do software.



## Repositorios
Obter novas listas de pacotes.
```sh
apt-get update
```

Executar uma atualização.
```sh
apt-get upgrade
```

Atualizar a distribuição.
```sh
apt-get dist-upgrade
```

Esses são os comando necessários para sempre manter seu sistema atualizado.



## Instalando programas
Para instalar um pacote vamos usar o **apt-get install** seguido do nome do pacote que queremos instalar.
```sh
apt-get install nmap
```



## Removendo programas
Para remover um pacote vamos usar o **apt-get remove** seguido do nome do pacote.
```sh
apt-get remove nmap
```

Podemos também usar a opção **purge** , ela é responsável por remover pacotes e ficheiros de configuração

```sh
apt-get remove nmap --purge
```



## Instalando pacote no formato **.deb**
Para instalar o pacote no formato **.deb** vamos usar o **dpkg**.

Dpkg é uma ferramenta para instalar, construir, remover e gerenciar pacotes Debian.

Para instalar um pacote
```sh
dpkg -i nomedoarquivo.deb
```

Ou pode ver os arquivos já instalados **.deb**
```sh
dpkg -l
```



## Buscando pacotes
O apt-cache é uma ferramenta de baixo nível utilizada para questionar informação dos ficheiros de cache binários do APT.
```sh
apt-cache search
```

Exemplo básico de uso.
```sh
apt-cache search tor
```



## Servidor LAMP (Linux , Apache , Mysql e PHP)
Vamos criar um servidor LAMP de forma simples.

Instalando **Apache**
```sh
apt-get install apache2
```

Instalando **Mysql**
```sh
apt-get install mysql-server
```

Instalando **PHP**
```sh
apt-get install php5
```

Precisamos agora instalar a biblioteca para interagir com o Mysql.
```sh
apt-get install php5-mysql
```



## Instalando TOR e configurando o Hidden Service
Vamos instalar o **TOR** e configurando o **Hidden Service** e redirecionar o apache.
```sh
apt-get install tor
```

Depois de instalado vamos ir até o diretório **/etc/tor/** , vamos ver que temos o arquivo **torrc**.

Por motivo de segurança vamos fazer um back , mais como ?

```sh
sudo cp /etc/tor/torrc /etc/tor/torrc-BKP
```

Com um editor de texto vamos modificar o arquivo nas seguintes linhas.

```sh
HiddenServiceDir /var/lib/tor/hidden_service/
HiddenServicePort 80 127.0.0.1:80

```

Vamos dar um restart no TOR
```sh
service tor restart
```

E vamos até o diretório **/var/lib/tor/hidden_service/**

Vamos ver que temos 2 arquivos , o principal é o **hostname**.

**hostname** é o nome do nosso arquivo que tera o domínio TOR criado que esta disponível na deepweb.

Agora é só acessar com o Tor Browser.
