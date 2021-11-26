### Set vm.max_map_count to at least 262144edit
The vm.max_map_count kernel setting must be set to at least 262144 for production use.

How you set vm.max_map_count depends on your platform:

- Linux

    The vm.max_map_count setting should be set permanently in /etc/sysctl.conf:

    ```
    grep vm.max_map_count /etc/sysctl.conf
    vm.max_map_count=262144
    ```

    To apply the setting on a live system, run:
    ```
    sysctl -w vm.max_map_count=262144
    ```

- macOS with Docker for Mac

    The vm.max_map_count setting must be set within the xhyve virtual machine:

    a. From the command line, run:

    ```
    screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty
    ```
    b. Press enter and use`sysctl` to configure vm.max_map_count:
    ```
    sysctl -w vm.max_map_count=262144
    ```
    To exit the screen session, type Ctrl a d.
- Windows and macOS with Docker Desktop

    The vm.max_map_count setting must be set via docker-machine:
    ```
    docker-machine ssh
    sudo sysctl -w vm.max_map_count=262144
    ```
- Windows with Docker Desktop WSL 2 backend

    The vm.max_map_count setting must be set in the docker-desktop container:
    ```
    wsl -d docker-desktop
    sysctl -w vm.max_map_count=262144
    ```