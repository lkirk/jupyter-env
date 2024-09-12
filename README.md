# Jupyter Env

My jupyterlab setup, complete with kernels, a systemd service and a script for
creating virtual environments.

## Installation

Install the systemd unit for the user

```bash
ln -s $(pwd)/etc/jupyterlab.service ~/.config/systemd/user
systemctl --user daemon-reload
```

Setup the jupyterlab env file for systemd
```bash
cat '
JUPYTERLAB_NOTEBOOK_NUM="1"
JUPYTERLAB_IP="<your ip>"
' > ~/.config/systemd/user/jupyterlab.service.env
```

Install the kernel specs into the user home

```bash
ln -s $(pwd)/share/jupyter/kernels ~/.local/share/jupyter
```

Create virtual environment for jupyterlab (see `--help` for more)

```bash
./scripts/make-notebook-ve
```

## Running

Start the service

```bash
systemctl --user start jupyterlab.service
```

Check up on the service

```bash
systemctl --user status jupyterlab.service
```

Checking the logs

```bash
journalctl --user -xu jupyterlab.service
```
