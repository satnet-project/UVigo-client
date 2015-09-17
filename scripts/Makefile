
all:
	@(cd sipgen; $(MAKE))
	@(cd siplib; $(MAKE))

install:
	@(cd sipgen; $(MAKE) install)
	@(cd siplib; $(MAKE) install)
	@test -d $(DESTDIR)/home/sgongar/Dev/client/.venv/lib/python2.7/site-packages || mkdir -p $(DESTDIR)/home/sgongar/Dev/client/.venv/lib/python2.7/site-packages
	cp -f sipconfig.py $(DESTDIR)/home/sgongar/Dev/client/.venv/lib/python2.7/site-packages/sipconfig.py
	cp -f /home/sgongar/Dev/client/scripts/sip-4.16.8/sipdistutils.py $(DESTDIR)/home/sgongar/Dev/client/.venv/lib/python2.7/site-packages/sipdistutils.py

clean:
	@(cd sipgen; $(MAKE) clean)
	@(cd siplib; $(MAKE) clean)
