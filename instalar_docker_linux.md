# Instalar o docker no linux

Remover qualquer instalação que possa existir

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

 Atualizar repositórios apt-get

```bash
sudo apt-get update
```
instale pacotes para permitir apto uso de um repositório por HTTPS:

```bash
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

Adicione a chave GPG oficial do Docker:

```bash
sudo mkdir -p /etc/apt/keyrings
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

Use o seguinte comando para configurar o repositório:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```bash
sudo apt-get update
```

Recebendo um erro GPG ao executar apt-get update?

Seu umask padrão pode estar configurado incorretamente, impedindo a detecção do arquivo de chave pública do repositório. Tente conceder permissão de leitura para o arquivo de chave pública do Docker antes de atualizar o índice do pacote:

```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
sudo apt-get update
```

Instale o Docker Engine, containerd e o Docker Compose.

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

Testando 

```bash
sudo docker run hello-world
```

## Possíveis problemas

error
```bash
Cannot connect to the docker daemon at unix:///var/run/docker .sock
```

solução
```bash
sudo service docker status
sudo service docker start
```

----------------------------------------------------------

error
```bash
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.40/containers/json: dial unix /var/run/docker.sock: connect: permission denied


```

solução

Cria o grupo docker (pode ser que já estaja criado) 

```bash
sudo groupadd docker
```

Adicionar seu usuário ao grupo criado.

```bash
sudo usermod -aG docker ${USER}
```

Execute o seguinte comando ou Logout, efetue login novamente e execute (se isso não funciona, pode ser necessário reiniciar sua máquina primeiro)

```bash
newgrp docker
```

Testar 

```bash
docker run hello-world
```