# CKAD environment and shell modifications

## Mute volume

- During the exam, the proctor will only communicate with you via the chat window.
- The proctor DOES want the microphone active to hear if you are mouthing the questions.
- You do not need the speakers — in my case I had feedback sound for the duration of the exam.
- Go ahead and mute the speakers before the exam starts to avoid feedback during the exam.

<br />

## CKAD shell modifications

### .bashrc

[CKA & CKAD environment](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad#cka-and-ckad-environment)

For your convenience, all environments — in other words, the base system and the cluster nodes — have the following additional command-line tools pre-installed and pre-configured:

- `kubectl` with `k` alias and Bash autocompletion:
  - `source <(kubectl completion bash)`
  - `alias k=kubectl`
  - `complete -F __start_kubectl k`
- `jq` for YAML/JSON processing
- `tmux` for terminal multiplexing
- `curl` and `wget` for testing web services
- `man` and man pages for further documentation

You are able to modify the `.bashrc` to add aliases and exports to assist you in the CKAD exam. The `.bashrc` file is a script that is executed when a user logs in.

```bash
# Optional but good practice — make a backup of the .bashrc
cp .bashrc .bashrc-original
```

```bash
# Edit the .bashrc file
vi ~/.bashrc
```

kubernetes.io bookmark: [kubectl autocomplete](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#bash)

```bash
# Aliases
alias cls=clear # Or "CTRL+L" clears the screen
alias kga="kubectl get all"

# Short aliases to set/show context/namespace.
# Only works for bash and bash-compatible shells.
# Set the current context with kx before using kn to set the namespace.
alias kx='f() { [ "$1" ] && kubectl config use-context $1 || kubectl config current-context ; } ; f'
alias kn='f() { [ "$1" ] && kubectl config set-context --current --namespace $1 || kubectl config view --minify | grep namespace | cut -d" " -f6 ; } ; f'

# Usage for kn:
#   kn               - prints current namespace
#   kn my-namespace  - changes into <my-namespace>

# Exports
export do="--dry-run=client -o yaml"
export kfc="kubectl apply -f" # kfc is delicious and makes me happy; feel free to change to kaf
export now="--force --grace-period=0"
export krr="kubectl run remote-run --image=busybox --restart=Never --rm -it --"
```

The first two exports save keystrokes on `--dry-run=client -o yaml` and `kubectl apply -f`:

- `kubectl create deploy my-deploy --image=nginx --replicas=3 --port=80 $do > my-deploy.yml`
- `$kfc my-deploy.yml`

The last export provides an in-cluster diagnostics Pod:

- `$krr wget -qO- <service>:8080`

```bash
# Initialize the .bashrc file
. .bashrc
```

<br />

### .vimrc (optional)

- You are able to modify the `.vimrc` to avoid indentation and syntax issues.
- The `.vimrc` file contains optional runtime configuration settings to initialize Vim when it starts.

```bash
vi ~/.vimrc
```

To make vi use two spaces for a tab, edit:

```bash
set expandtab
set tabstop=2
set shiftwidth=2
```

Explanation:

- The `expandtab` property ensures that when you hit tab, vi will use spaces.
- The `tabstop` and `shiftwidth` properties cause vi to use tabs with a width of 2 characters for indenting.

_End of Section_
