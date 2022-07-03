    # Use root/example as user/password credentials
    version: '3.1'

    services:

    db:
        image: mysql
        command: --default-authentication-plugin=mysql_native_password
        restart: always
        environment:
        MYSQL_ROOT_PASSWORD: root
        MYSQL_DATABASE: main
        ports:
        - 3306:3306
        volumes:
        - "./config/my.conf:/etc/mysql/conf.d/config-file.cnf"
        - "./sqldata:/var/lib/mysql:rw"
    adminer:
        image: adminer
        restart: always
        ports:
        - 8090:8080
    redis:
        image: "redis:alpine"
        restart: always
        ports:
        - 6379:6379


    # Use root/example as user/password credentials
    version: '3.1'

    services:

    db:
        image: mysql
        command: --default-authentication-plugin=mysql_native_password
        restart: always
        environment:
        MYSQL_ROOT_PASSWORD: root


    adminer:
        image: adminer
        restart: always
        ports:
        - 8080:8082
