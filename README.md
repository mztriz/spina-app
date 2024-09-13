# README

> A simple SpinaCMS setup running in Docker, configurable for development or production environments. Easily deploy SpinaCMS with PostgreSQL using Docker Compose.

## Dir Structure

### Key files

```plaintext
.
├── Dockerfile                   # Dockerfile for building SpinaCMS
├── README.md                    # This doc
├── docker-compose.yml           # Docker Compose file to define and run Rails and Postgres
├── run.log                      # Log file generated by run.sh script
├── run.sh                       # Main script to run and manage Docker containers
├── setup.sh                     # Script to wait for PostgreSQL and configure SpinaCMS
```

* **`run.sh` / `run.log`** :
  Script that handles loading environment variables, building, and starting containers. Logs are saved to `run.log`.
* **`Dockerfile`** :
  Defines the application environment and installation of dependencies needed to run SpinaCMS.
* **`docker-compose.yml`** :
  Defines multi-container setup for Rails and Postgres
* **`.env.dev` / `.env.prod`** :
  Environment files containing configurations for development and production setups.

## Getting started

###Prereqs

Docker and Docker Compose

### Running the app

####Get the code

```bash
git clone https://github.com/mztriz/spina-app.git
cd spina-app
```

#### Run the code
Run the run.sh script with the appropriate environment (dev for development or prod for production)

```bash
chmod +x run.sh
./run.sh [dev | prod]
```

This command will set the environment (using `.env.dev` or .`env.prod`),remove any old docker-compose volumes (using`docker-compose down -v`) and finally and start the containers.

Once the `run.sh` script outputs

>> Docker containers started successfully

in the terminal  you can check the rest of the progress of the containers with `docker-compose ps`, `docker-compose logs db` and `docker-compose logs web`. It typically takes 1-2 minutes after running `run.sh` for the Rails site to actually be available.

After Rails is running, the app can be reached at either
[http://localhost:3000](http://localhost:3000) (dev) or [https://localhost](https://localhost) (prod).

In the development environemnt the `/admin` panel is available at [http://localhost:3000/admin](http://localhost:3000) and the login information is available in [seeds.rb](./seeds.rb).

## Demo
Running `run.sh` for dev and prod
![Demo](./assets/Kapture%202024-09-12%20at%2017.06.32.gif)

I forgot to show the admin panel
![AdminPanel](./assets/Kapture%202024-09-12%20at%2017.13.09.gif)