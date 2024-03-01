run docker compose up -d
then after the container has started run the db script
service db start
you can access all selected services
INSTALLVALUE variable in the entrypoint.sh file is used to select the suites you want installed. (that will be moved to an envirnmental variable in later release)
