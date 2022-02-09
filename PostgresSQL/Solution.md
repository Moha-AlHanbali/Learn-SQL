# Exercises Solution (MySQL)

## Setup

- Follow this [guide](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database) to install PostgresSQL on WSL2.

- Install  [MySQL](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2) Extension on `VSCode`.

- Run the command `$ sudo service postgresql start`.

- Run the command `$ sudo -u postgres psql`.

- Create a new connection with the extension, using the credentials you created while installing PostgreSQL earlier. Make sure you choose server type as `PostgresSQL`.

- In Postgres Shell, create a new Database `# create database "LearnSQL"`.

- Quit the shell`# \q`.

- Enter the following command `$ psql -h 127.0.0.1 -U postgres "LearnSQL" < sqlexbackup.sql` or `psql -h 127.0.0.1 -U postgres "LearnSQL" < northwindexbackup.sql`, you might need to replace the backup with it's full path extension.

- Enter the following: 
  - `$ psql -h 127.0.0.1 -U postgres "LearnSQL"`.
  - `# CREATE ROLE root WITH LOGIN ENCRYPTED PASSWORD 'password';`.
  - `# GRANT CONNECT ON DATABASE "LearnSQL" TO root;`.
  - `# GRANT USAGE ON SCHEMA public TO root;`.
  - `# GRANT SELECT ON ALL TABLES IN SCHEMA public TO root;`.
  - `# \q`.

- Enter `$ psql -h 127.0.0.1 -U root "LearnSQL"` to start executing SQL commands in terminal or use a `VSCode` extension.
