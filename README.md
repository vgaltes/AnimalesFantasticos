# RUNNING ON MAC

## Pre-requisites
Docker: [Installation instructions](https://docs.docker.com/docker-for-mac/install/)
MySql client: the easiest way to install it is using `brew install mysql`. This will install the client and the server but you can uninstall it after the workshop using `brew uninstall mysql`

## Starting the database
Run the following command: `docker-compose up -d`
This will start a MySql server in the background

## Initialising the database
Wait until you see the folder `mysqlData` in your project root folder (shouldn't take more than 30 seconds)
Run the following command in case you're using the CLI: `mysql -h 127.0.01 -P 3306 -u root -pMyLocalPassword < Scripts/AnimalesFantasticos.sql`
If you're using some sort of GUI, use it to run the script on `Scripts/AnimalesFantasticos.sql`.

This will create the database and fill it with some test data.

## Scaffold the DBContext
Restore the packages of the solution: `dotnet restore`
Check that the Entity Framework CLI Tool is installed by running: `dotnet ef --help`
CD into the DBContext project: `cd AnimalesFantasticosDBContext`
Run the following command: `dotnet ef dbcontext scaffold "Server=127.0.0.1;User Id=root;Password=MyLocalPassword;Database=AnimalesFantasticos" Pomelo.EntityFrameworkCore.MySql -o Models`
