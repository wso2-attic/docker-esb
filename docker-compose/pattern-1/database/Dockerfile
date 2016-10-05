FROM mysql:5.5

COPY artifacts/esbdb.sql /docker-entrypoint-initdb.d/
COPY artifacts/analyticsdb.sql /docker-entrypoint-initdb.d/

EXPOSE 3306
