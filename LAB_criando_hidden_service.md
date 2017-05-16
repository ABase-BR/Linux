# Primeiros passos com Hidden Service TOR
DeepWeb Servidor
  - Instalando TOR
  - Criando Hidden Service


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
