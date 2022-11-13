# Instalar zsh e oh my zsh

Atualizar lista de repositório apt-get

```bash
 sudo apt-get update
```

Se não tiver git instalado

```bash
apt-get install git
```

Se não tiver curl instalado

```bash
sudo apt install curl
```

Instalar o zsh

```bash
sudo apt install zsh
```

Instalar oh my zsh

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Se não tiver vim instalado

```bash
sudo apt install vim
```

 Editar o arquivo `.zshrc` para mudar o tema caso queira. (Eu gosto o `obraun`).


Instalar o zinit

```bash
bash -c "$(curl --fail --show-error --silent --location https://raw.githubusercontent.com/zdharma-continuum/zinit/HEAD/scripts/install.sh)"
```


Colar o conteúdo abaixo no arquivo `.zshrc`.

```
zinit light zdharma/fast-syntax-highlighting
zinit light zsh-users/zsh-autosuggestions
zinit light zsh-users/zsh-completions
```