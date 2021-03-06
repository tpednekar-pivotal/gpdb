MODULE_big = gphdfs
OBJS       = gphdfsformatter.o gphdfsprotocol.o

PG_CPPFLAGS = -I$(libpq_srcdir)
PG_LIBS = $(libpq_pgport)

ANT = ant
ANT_OPTS="-Djavax.net.ssl.trustStore=../../releng/make/dependencies/cacerts"

PG_CONFIG := pg_config
PGXS := $(shell $(PG_CONFIG) --pgxs)
include $(PGXS)

JAR_FILES = dist/gphd-1.0-gnet-1.0.0.1.jar \
	dist/gphd-1.1-gnet-1.1.0.0.jar \
	dist/gpmr-1.0-gnet-1.0.0.1.jar \
	dist/gpmr-1.2-gnet-1.0.0.1.jar \
	dist/cdh3u2-gnet-1.1.0.0.jar \
	dist/gphd-1.2-gnet-1.1.0.0.jar \
	dist/cdh4.1-gnet-1.2.0.0.jar \
	dist/gphd-2.0.2-gnet-1.2.0.0.jar

JAVADOC_TARS = gnet-1.1-javadoc.tar gnet-1.0-javadoc.tar

all: $(JAR_FILES) $(JAVADOC_TARS)

dist/gphd-1.0-gnet-1.0.0.1.jar:
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) dist -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=0.20.1-gphdce-1.0.0.0 \
                -Dgphdgnet.version=gphd-1.0-gnet-1.0.0.1 \
                -Dgpgnet.src=1.0

dist/gphd-1.1-gnet-1.1.0.0.jar:
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) dist -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=0.20.205.0-gphd-1.1.0.0 \
                -Dgphdgnet.version=gphd-1.1-gnet-1.1.0.0 \
                -Dgpgnet.src=1.1

dist/gpmr-1.0-gnet-1.0.0.1.jar:
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) dist -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=0.20.2 \
                -Dgphdgnet.version=gpmr-1.0-gnet-1.0.0.1 \
                -Dgpgnet.src=1.0

#gpmr-1.2 uses hadoop-core-2.0.0-mr1-cdh4.1.2.jar to build, the same as cdh4.1
dist/gpmr-1.2-gnet-1.0.0.1.jar:
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) dist -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=2.0.0-mr1-cdh4.1.2 \
                -Dhadoop-common.revision=2.0.0-cdh4.1.2 \
                -Dgphdgnet.version=gpmr-1.2-gnet-1.0.0.1 \
                -Dgpgnet.src=1.2 \
                -Dgpgnet.configuration=hadoop2

dist/cdh3u2-gnet-1.1.0.0.jar:
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) dist -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=0.20.2-cdh3u2 \
                -Dgphdgnet.version=cdh3u2-gnet-1.1.0.0 \
                -Dgpgnet.src=1.1

dist/gphd-1.2-gnet-1.1.0.0.jar:
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) dist -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=1.0.3-gphd-1.2.0.0 \
                -Dgphdgnet.version=gphd-1.2-gnet-1.1.0.0 \
                -Dgpgnet.src=1.1

dist/cdh4.1-gnet-1.2.0.0.jar:
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) dist -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=2.0.0-mr1-cdh4.1.2 \
                -Dhadoop-common.revision=2.0.0-cdh4.1.2 \
                -Dgphdgnet.version=cdh4.1-gnet-1.2.0.0 \
                -Dgpgnet.src=1.2 \
                -Dgpgnet.configuration=hadoop2

dist/gphd-2.0.2-gnet-1.2.0.0.jar:
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) dist -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=2.0.2-alpha-gphd-2.0.1.0 \
                -Dhadoop-common.revision=2.0.2-alpha-gphd-2.0.1.0 \
                -Dgphdgnet.version=gphd-2.0.2-gnet-1.2.0.0 \
                -Dgpgnet.src=1.2 \
                -Dgpgnet.configuration=hadoop2

unittest: $(JAR_FILES)
	$(ANT) clean
	ANT_OPTS=$(ANT_OPTS) $(ANT) test -Dorg=apache \
                -Dname=hadoop-core \
                -Drevision=2.0.0-mr1-cdh4.1.2 \
                -Dhadoop-common.revision=2.0.0-cdh4.1.2 \
                -Dgphdgnet.version=cdh4.1-gnet-1.2.0.0 \
                -Dgpgnet.src=1.2 \
                -Dgpgnet.configuration=ut

gnet-1.1-javadoc.tar: $(JAR_FILES)
	$(ANT) javadoc -Dorg=apache \
                   -Dname=hadoop-core \
                   -Drevision=0.20.205.0-gphd-1.1.0.0 \
                   -Dgphdgnet.version=gnet-1.1 \
                   -Dgpgnet.src=1.1
	$(TAR) -cf gnet-1.1-javadoc.tar gnet-1.1-javadoc

gnet-1.0-javadoc.tar:  $(JAR_FILES)
	$(ANT) javadoc -Dorg=apache \
                   -Dname=hadoop-core \
                   -Drevision=0.20.2 \
                   -Dgphdgnet.version=gnet-1.0 \
                   -Dgpgnet.src=1.0
	$(TAR) -cf gnet-1.0-javadoc.tar gnet-1.0-javadoc

install-jars: $(JAR_FILES)
	$(INSTALL_PROGRAM) dist/*.jar '$(DESTDIR)$(libdir)/hadoop/'
	$(INSTALL_PROGRAM) hadoop_env.sh$(X) '$(DESTDIR)$(libdir)/hadoop/hadoop_env.sh$(X)'

.PHONY: install-javadocs
install-javadocs: $(JAVADOC_TARS)
	$(INSTALL_DATA) *-javadoc.tar '$(DESTDIR)$(docdir)/javadoc'

.PHONY: install-gphdfs.so
install-gphdfs.so:
	$(INSTALL_PROGRAM) gphdfs.so $(DESTDIR)$(pkglibdir)

.PHONY: install-data
install-data:
	$(INSTALL_DATA) gphdfs.sql '$(DESTDIR)$(datadir)/cdb_init.d/gphdfs.sql'

install: install-jars install-javadocs install-gphdfs.so install-data

installdirs:
	$(MKDIR_P) '$(DESTDIR)$(libdir)/hadoop'
	$(MKDIR_P) '$(DESTDIR)$(docdir)/javadoc'

uninstall:
	rm -f '$(DESTDIR)$(bindir)/*.jar'
	rm -f '$(DESTDIR)$(bindir)/hadoop_env.sh$(X)'
	rm -f '$(DESTDIR)$(datadir)/cdb_init.d/gphdfs.sql'

clean: clean-extras

clean-extras:
	$(ANT) clean
	rm -rf *-javadoc
	rm -f *-javadoc.tar
	rm -rf result
