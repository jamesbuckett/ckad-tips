## CKAD Shell Modifications

### .bashrc

- You are able to modify the .bashrc to add alias and exports to assist you in the CKAD exam.
- The .bashrc file is a script file that's executed when a user logs in

```bash
# Optional but good practice - make a backup of the .bashrc
cp .bashrc .bashrc-original
```

```bash
# Edit the .bashrc file
vi ~/.bashrc
```

kubernetes.io bookmark: [Kubectl autocomplete](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#bash)

```bash
# kubectl autocomplete with alias
source <(kubectl completion bash)
alias k=kubectl
complete -F __start_kubectl k

# Alias
alias cls=clear
alias kga="kubectl get all"

# Exports
export do="--dry-run=client -o yaml"
export kfc="kubectl apply -f" # kfc is delicious and makes me happy, feel free to change to kaf
export krr="kubectl run remote-run --image=busybox --restart=Never --rm -it --"
```

The first two exports are to save keystrokes.

Example use: - kubectl create deploy my-deploy --image=nginx --replicas=3 --port=80 `$do` > my-deploy.yml - `$kfc` my-deploy.yml

The last export is to provide an in cluster remote run capability. - `$krr` wget -qO- <service>:8080

```bash
# Initialize the .bashrc file
. .bashrc
```

### .vimrc

    * You are able to modify the .vimrc to avoid indentation and syntax issues.
    * The .vimrc file contains optional runtime configuration settings to initialize Vim when it starts.

```bash
vi ~/.vimrc
```

To make vi use two spaces for a tab edit.

```bash
set expandtab
set tabstop=2
set shiftwidth=2
```

Explanation

- The `expandtab` property will ensure that when you hit tab it will actually use spaces.
- The `tabstop` and `shiftwidth` property causes vim to use tabs with a width of 2 characters for indenting

_End of Section_
