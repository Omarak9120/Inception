FROM debian:bullseye

# Install required packages
RUN apt-get update && apt-get upgrade -y && apt-get install -y mariadb-server netcat

# Create directory for MariaDB socket
RUN mkdir -p /run/mysqld && chown -R mysql:mysql /run/mysqld

# Copy initialization script
COPY mariadb_script.sh /mariadb_script.sh
RUN chmod +x /mariadb_script.sh

# Expose MariaDB port
EXPOSE 3306

# Set the entrypoint
ENTRYPOINT ["./mariadb_script.sh"]
