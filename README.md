#                     --NOTES--

                --GITHUB--
git config --global user.name "ususario"
git config --global user.email "correo"
1.- ssh-keygen -t rsa -b4096 -C 'tucorreo@.com'
2.- eval "$(ssh-agent -s)"
3.- cat ~/.ssh/id_rsa.pub

                --PHPMYADMIN--
sudo /opt/lampp/lampp start
cd /opt/lampp
sudo ./manager-linux-x64.run

        --FUNCIONES TERMINAL--
tty-clock -C   reloj
ranger  explorador
tmux    dividir terminal
nano ~/.bashrc  crear atajos rerminal

        --ATAJOS TERMINAL--
nano ~/.bashrc #abrir archivo atajos

alias ll='ls -alF'
alias gcmt='git commit -m'
alias gcl='git clone'
alias gadd='git add'

source ~/.bashrc #cargar atajos

https://github.com/cronwell30

https://www.youtube.com/watch?v=5kWLE1Eu7LU

---------------------------------------------------------------------
#                postgres

        --Instalar PostgreSQL--
sudo apt install postgresql postgresql-contrib

            --Verificar estado del servicio--
sudo systemctl status postgresql

            --Vercion--
psql --version

        --Habilitar inicio automático--
sudo systemctl enable postgresql

        --Acceder a consola como super usuario--
sudo -i -u postgres
psql

        --Habilitar inicio automático--
sudo systemctl enable postgresql

        --Cambiar usuario--
sudo -i -u user name

#               users

        -- Crear un nuevo usuario/rol
CREATE USER mi_usuario WITH PASSWORD 'tu_contraseña';

        --otorgar todos los permisos a un usuario--
ALTER USER mi_usuario WITH SUPERUSER CREATEDB CREATEROLE REPLICATION INHERIT LOGIN;

            --lista de usuarios--
\du

        --Cambiar usuario--
sudo -i -u user name

        -- Otorgar privilegios específicos a un ususrio --
    CREATEDB    -- Puede crear bases de datos
    CREATEROLE  -- Puede crear roles
    LOGIN       -- Puede conectarse
    VALID UNTIL '2025-12-31';  -- Expiración opcional


#MODIFICACION DE USUARIOS

            -- Cambiar contraseña--
ALTER USER nombre_usuario WITH PASSWORD 'nueva_contraseña';

        -- Cambiar fecha de expiración--
ALTER USER nombre_usuario VALID UNTIL 'infinity';

            -- Renombrar usuario--
ALTER USER nombre_usuario RENAME TO nuevo_nombre;

        -- Eliminar usuario con todos sus objetos--
DROP USER nombre_usuario CASCADE;

#           PRIVILEGIOS

-- Verificar tus propios privilegios
SELECT current_user, usesuper FROM pg_user WHERE usename = current_user;

                --Agregar privilegios--
ALTER USER nombre_usuario CREATEDB CREATEROLE;

                -- Quitar privilegios--
ALTER USER nombre_usuario NOCREATEDB NOCREATEROLE;

                --Otorgar todos los privilegios a un usuario--
ALTER USER mi_usuario WITH SUPERUSER CREATEDB CREATEROLE REPLICATION INHERIT LOGIN;

#       CONEXIONES

1.- Conecta como super usuario
2.- Crea base de datos
3.- Crear y ortorgar privilegios a usuario (en caso de no haber creado previamente)

                -- Edita archivo configuracion postgres--

sudo nano /etc/postgresql/*/main/postgresql.conf
Busca la línea #listen_addresses = 'localhost' y cámbiala por listen_addresses = '*'

                --Edita el archivo de control de acceso de clientes:--

sudo nano /etc/postgresql/*/main/pg_hba.conf

                --Agrega esta linea al final del archivo--
host    all             all             0.0.0.0/0               md5

                --Reinicia el servicio--
sudo systemctl restart postgresql

prueba commit
