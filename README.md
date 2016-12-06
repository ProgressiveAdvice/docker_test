# docker_test

Ez alapján készítve: [https://hub.docker.com/_/php/](https://hub.docker.com/_/php/)

## Lépések:
 * `aron.php` elkészítése. Ez az a fájl amit le akarunk futtatni
 * `Dockerfile` elkészítése. Ez a fájl írja le, hogy miként "buildelje" le a docker az imageünket
 * `docker build -t aron_specko_tagje .`
 * `docker -it --rm --name aron_containerje aron_specko_tagje`
 
Először gond volt az aron.php tartalmával, mert kimaradtak a <php tagek a file eljéről és végéről. Ez azt eredményezte, hogy
kiokádta csak a file tartalmát a futtatáskor a docker image.
Ezek után módosítottuk az aron.php tartalmát, hogy a tényleges számításunkat végezze el. A probléma ezek után az lett, hogy
a választott megoldás (COPY-val másoljuk be a fájlt az image-be) miatt újra kell buildelnünk az imaget. Ha a volume mountolást
választottuk volna, akkor image újrabuildelés nélkül áthidalhattuk volna ezt a problémát

## Lépések az újrabuildeléshez (csak meg kell ismételni az utolsó 2 lépéset):
 * `docker build -t aron_specko_tagje .`
 * `docker -it --rm --name aron_containerje aron_specko_tagje`
