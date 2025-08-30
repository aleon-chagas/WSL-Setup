# 🚀 Setup WSL2 Ubuntu 24.04 LTS – DevOps/SRE

## 🎯 Sobre o Projeto

Este playbook Ansible automatiza a configuração inicial do **Ubuntu 24.04 LTS** rodando no **WSL2**, preparando um ambiente pronto para profissionais de DevOps e SRE.
Inclui desde a instalação do Ansible (como pré-requisito) até a configuração de utilitários de sistema, ferramentas Kubernetes, CLIs de cloud, ferramentas essenciais de DevOps, e customização do ambiente do usuário com Oh-My-Zsh e Powerlevel10k.

> ⚠️ **Importante:** Execute este playbook em uma instalação limpa do Ubuntu 24.04 no WSL2, com privilégios sudo.

***

## 🐍 Instalação do Ansible (Pré-requisito)

Para isolar o Ansible e garantir compatibilidade, recomenda-se instalá-lo em um ambiente virtual Python conforme o passo a passo abaixo:

```bash
# Atualize o sistema e instale dependências
sudo apt update && sudo apt upgrade -y
sudo apt install python3-venv sshpass -y


# Crie o ambiente virtual
python3 -m venv pyenv


# Ative o ambiente virtual
source pyenv/bin/activate


# Atualize pip e instale Ansible
pip install --upgrade pip
pip install ansible


# Verifique a instalação
ansible --version
```

Para entrar novamente no ambiente virtual:

```bash
source pyenv/bin/activate
```

Para sair do ambiente virtual:

```bash
deactivate
```


***

## 🚀 Como Usar

1. Clone este repositório:
```bash
git clone <URL-DO-REPOSITORIO>
cd <PASTA-CLONADA>
```

2. Ative seu ambiente virtual Python com Ansible instalado:
```bash
source pyenv/bin/activate
```

3. Execute o playbook:
```bash
ansible-playbook setup_wsl.yml -K
```

O parâmetro `-K` solicitará a senha sudo necessária para executar tarefas privilegiadas.

***

## 📦 Softwares e Ferramentas Instaladas

| Categoria | Ferramentas |
| :-- | :-- |
| **Sistema Base** | curl, gnupg, lsb-release, nala, build-essential, vim, git, jq, httpie, htop, ncdu, tree, zsh, tmux |
| **Kubernetes** | kubectl, k9s, kubectx, kubens |
| **Cloud \& DevOps** | PowerShell, Azure CLI, AWS CLI v2, yq |
| **Terminal Shell** | Oh-My-Zsh, Powerlevel10k, plugins: syntax-highlighting, autosuggestions, k, zsh-completions |
| **Containers** | Docker (via dependências pré-instaladas no WSL) |

> O ambiente está otimizado para uso produtivo e desenvolvimento, com integração Kubernetes e ferramentas DevOps.

***

## ⚙️ Personalização e Plugins Zsh

- O Oh-My-Zsh é instalado automaticamente no diretório do usuário.
- O tema Powerlevel10k é configurado como padrão.
- Plugins essenciais para produtividade no shell são clonados e configurados:
    - `zsh-syntax-highlighting`
    - `zsh-autosuggestions`
    - `k`
    - `zsh-completions`

***

## 🎨 Personalização

- Edite as variáveis `base_packages`, `util_packages` e `devops_apps` no arquivo `setup_wsl.yml` conforme suas necessidades.
- Adapte ou remova blocos para adequar ao seu fluxo de trabalho.

***

### 📝 Otimizando o VIM global para YAML

Abra e edite o arquivo global do Vim para facilitar a edição de YAML e melhorar a visualização:

```bash
sudo vim /etc/vim/vimrc +$
```

Adicione ao final do arquivo:

```vim
" YAML Resources

set cursorline
set cursorcolumn
set number
set paste

" Indentação ideal para YAML
autocmd FileType yaml setlocal ts=2 sts=2 sw=2 expandtab
```

Essas configurações proporcionam destaque visual de linha e coluna, numeração, melhor colagem de código e indentação correta para arquivos YAML, seguindo as melhores práticas para edição de playbooks Ansible e infraestrutura como código.

***

## 📜 Licença

Este projeto está sob a licença **MIT**. Consulte o arquivo LICENSE para mais detalhes.

***

> Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests 😄