## CKAD Shell Modifications

### .bashrc

You are able to modify the .bashrc to add alias and exports to assist you in the CKAD exam.

```bash
# First make a backup of the .bashrc
cp .bashrc .bashrc-original
```

```bash
# Edit the .bashrc file
vi ~/.bashrc
```

```bash
alias cls=clear
alias k=kubectl
alias kga="kubectl get all"

export do="--dry-run=client -o yaml"
export kfc="kubectl apply -f" # kfc is delicious and makes me happy, feel free to change to kaf
export krr="kubectl run remote-run --image=busybox --restart=Never --rm -i --"
```

The first two exports are to save keystrokes.

- `kubectl create deploy my-deploy --image=nginx --replicas=3 --port=80 $do > my-deploy.yml`
- `$kfc my-deploy.yml`

The last export is to provide an in cluster remote run capability.

- `krr curl <my-service>:8080`

```bash
# Initialize the .bashrc file
. .bashrc
```

### .vimrc

You are able to modify the .vimrc to avoid indentation and syntax issues.

```bash
vi ~/.vimrc
```

To make vi use two spaces for a tab edit.

```bash
set expandtab
set tabstop=2
set shiftwidth=2
```

_End of Section_
