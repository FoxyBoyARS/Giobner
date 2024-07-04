version: '3'

services:
  git-server:
    image: rockstorm/git-server
    container_name: git-server
    restart: unless-stopped

    environment:
      # Password for the git user
      GIT_PASSWORD: 'LoLoLo123LoLoLo123'

      # Path where the file with the password for the git user will be
      # mounted in the container in order to replace the default one
      # GIT_PASSWORD_FILE: /run/secrets/git_password

      # Setting this variable creates a link in the git user directory
      # to access repositories without absolute paths
      # REPOSITORIES_HOME_LINK: /srv/git

      # Path where the SSH host keys will be mounted in the container
      # in order to replace the default keys
      # SSH_HOST_KEYS_PATH: /tmp/host-keys

      # Set specific UID and GID for the git user
      # GIT_USER_UID: 1001
      # GIT_USER_GID: 1001

    volumes:
      # Folder with git repositories
      - git-repositories:/srv/git

      # File containing the SSH keys of clients that will be allowed
      # to use this service through a public key
      - ./.ssh/authorized_keys:/home/git/.ssh/authorized_keys

      # Configuration file for the OpenSSH daemon to use instead of
      # the one that is generated by default
      - ./sshd_config:/etc/ssh/sshd_config:ro

      # Disable interactive SSH login for the git user
      # - /executable/file:/home/git/git-shell-commands/no-interactive-login

    ports:
      - '2222:22'

  cgit:
    image: 'ankitrgadiya/cgit:debian-nginx'
    container_name: cgit
    volumes:
      - git-repositories:/git
    ports:
      - '80:80'

volumes:
  git-repositories:

  arr = [7,4,9,2,6,3]
insertionsort(arr)
print('Sorted %s'  %arr) # sorted [2, 3, 4, 6, 7, 9]
arr = [7,4,9,2,6,3]


