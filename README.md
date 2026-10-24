# ansible-arch-setup

Playbooks de Ansible para configurar máquinas Arch Linux después de una instalación limpia.

## ¿Qué hace?

- Actualiza la caché de `pacman` y los paquetes del sistema.
- Instala un conjunto de paquetes esenciales (git, vim, htop, tmux, etc.).
- Es **idempotente**: puedes ejecutarlo múltiples veces sin efectos secundarios.

## Requisitos

- **Nodo de control**: Arch Linux con `ansible` instalado (`sudo pacman -S ansible`).
- **Nodos gestionados**: Arch Linux con Python (`/usr/bin/python`) y SSH habilitado (`sudo systemctl enable --now sshd`).
- Acceso SSH sin contraseña desde el nodo de control (recomendado usar `ssh-copy-id`).

## Uso

1. Clona el repositorio:

   ```bash
    git clone https://github.com/TU_USUARIO/ansible-arch-setup.git
    cd ansible-arch-setup

2. Edita inventory.ini con las IPs y usuarios de tus máquinas.

3. Verifica la sintaxis.
   ```bash
    ansible-playbook site.yml --syntax-check

4. Simula los cambios.
   ```bash
    ansible-playbook site.yml --check --ask-become-pass

5. Aplica los cambios.
   ```bash
    ansible-playbook site.yml --ask-become-pass

## Personalización

Para instalar otros paquetes, edita roles/packages/defaults/main.yml y añade los que necesites a la lista essential_packages.

## Roadmap

- [x] Rol `packages`: instalación de paquetes esenciales
- [ ] Rol `user`: configuración de usuario y grupos
- [ ] Rol `dotfiles`: despliegue de configuraciones personales
- [ ] CI con GitHub Actions (syntax-check en cada push)
