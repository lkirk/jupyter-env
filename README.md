# Jupyter Env

My jupyterlab setup, complete with kernels, a systemd service and a script for
creating virtual environments.

## Installation

Install the systemd unit for the user

```bash
ln -s etc/jupyterlab.service ~/.config/systemd/user
systemctl --user daemon-reload
```

Install the kernel specs into the user home

```bash
ln -s $(pwd)/share/jupyter/kernels ~/.local/share/jupyter
```
