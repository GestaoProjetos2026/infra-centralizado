---

# 🧪 Testando a instalação do Docker

Após instalar os pacotes do Docker, execute os seguintes comandos para validar a instalação:

## Instalar os pacotes Docker

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Executar o container de teste

```bash
sudo docker run hello-world
```

---

# ✅ Resultado esperado

Se a instalação foi concluída com sucesso, o Docker exibirá uma mensagem semelhante a esta:

```text
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

Isso confirma que:

- O serviço Docker está funcionando
- Os containers conseguem ser executados corretamente
- A instalação dos pacotes foi realizada com sucesso
=======================================================================================================================================
---

# 🐙 Instalação do Docker Compose

O Docker Compose permite definir e executar aplicações multi-containers utilizando um arquivo `docker-compose.yml`.

## Atualizar os pacotes do sistema

```bash
sudo apt-get update
```

## Instalar o Docker Compose Plugin

```bash
sudo apt-get install -y docker-compose-plugin
```

---

# ✅ Validando a instalação do Docker Compose

Verifique se o Compose foi instalado corretamente:

```bash
docker compose version
```

---

# 🎉 Resultado esperado

O terminal deverá retornar algo semelhante a:

```text
Docker Compose version v2.x.x
```

Isso confirma que o Docker Compose foi instalado com sucesso e está pronto para uso.
=======================================================================================================================================
---

# ☸️ Instalação do K3s

O K3s é uma distribuição leve do Kubernetes desenvolvida pela Rancher, ideal para ambientes de desenvolvimento, laboratórios e servidores com poucos recursos.

## Instalando o K3s

Execute o comando abaixo para instalar o K3s utilizando o script oficial:

```bash
curl -sfL https://get.k3s.io/ | sh -
=======================================================================================================================================
---

# 🧪 Validando o cluster K3s

Após instalar o K3s, execute o comando abaixo para verificar os nós do cluster Kubernetes:

```bash
sudo k3s kubectl get nodes

NAME            STATUS   ROLES           AGE   VERSION
deploy-gp2026   Ready    control-plane   27s   v1.35.4+k3s1
=======================================================================================================================================
---

# ⚠️ Erro de permissão ao utilizar o kubectl

Ao executar o comando:

```bash
kubectl create namespace argocd

WARN[0000] Unable to read /etc/rancher/k3s/k3s.yaml, please start server with --write-kubeconfig-mode or --write-kubeconfig-group to modify kube config permissions
error: error loading config file "/etc/rancher/k3s/k3s.yaml": open /etc/rancher/k3s/k3s.yaml: permission denied
=======================================================================================================================================
---

# 📦 Criando o namespace do ArgoCD

Após configurar corretamente o acesso ao `kubectl`, foi executado o seguinte comando:

```bash
kubectl create namespace argocd

namespace/argocd created
=======================================================================================================================================
---

# 🚀 Instalando o ArgoCD no Kubernetes

Com o namespace criado, execute o comando abaixo para instalar o ArgoCD no cluster Kubernetes:

```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
