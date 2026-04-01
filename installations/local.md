# Instalación de Docker en Fedora

Eliminar versiones viejas de docker si antes ya lo tenias.

```bash
sudo dnf remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
```



Agregar repositorio de Docker a los paquetes de instalación de Fedora.

```bash
sudo dnf config-manager addrepo --from-repofile https://download.docker.com/linux/fedora/docker-ce.repo
```



Instalar los paquetes de Docker

```bash
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```



Iniciar Docker en tu maquina

```bash
sudo systemctl enable --now docker
```



Post-Instalación

Crear un grupo

```bash
sudo groupadd docker
```

Agregar nuestro usuario al grupo

```bash
sudo usermod -aG docker $USER 
```

Ejecutar el siguiente comando

```bash
newgrp docker
```

Verifica que puedes ejecutar comandos de Docker sin sudo.

```bash
docker run hello-world
```

