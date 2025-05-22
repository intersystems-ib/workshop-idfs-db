ARG IMAGE=containers.intersystems.com/intersystems/iris-community:latest-cd
FROM $IMAGE

USER root

WORKDIR /opt/irisapp
RUN chown -R irisowner:irisowner /opt/irisapp

RUN echo '' > /dump_Errors.log
RUN chmod +x /dump_Errors.log

RUN chown -R irisowner:irisowner /dump_Errors.log

USER irisowner

# copy files to image
WORKDIR /opt/irisapp
COPY --chown=irisowner:irisowner src src

COPY --chown=$ISC_PACKAGE_MGRUSER:$ISC_PACKAGE_IRISGROUP /iris/irissession.sh /
RUN chmod +x /irissession.sh

COPY --chown=$ISC_PACKAGE_MGRUSER:$ISC_PACKAGE_IRISGROUP /iris/sql/dump.txt /
RUN chmod +x /dump.txt

SHELL ["/irissession.sh"]

RUN \
zn "%SYS" \
set sc = $SYSTEM.OBJ.LoadDir("/opt/irisapp/src/Test", "ck", , 1) \
if sc do ##class(Test.Installer).Install() \
zn "TEST" \
DO $SYSTEM.SQL.Schema.ImportDDL("/dump.txt",,"IRIS") \