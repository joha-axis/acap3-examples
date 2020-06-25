PROG1	= vdo_larod
OBJS1	= $(PROG1).c argparse.c imgconverter.c imgprovider.c
PROGS	= $(PROG1)

PKGS = gio-2.0 vdostream gio-unix-2.0 liblarod

CFLAGS  += -Iinclude

LDLIBS  += -lyuv
LDFLAGS += -L./lib -Wl,-rpath,'$$ORIGIN/lib'

CFLAGS += $(shell PKG_CONFIG_PATH=$(PKG_CONFIG_PATH) pkg-config --cflags $(PKGS))
LDLIBS += $(shell PKG_CONFIG_PATH=$(PKG_CONFIG_PATH) pkg-config --libs $(PKGS))

CFLAGS += -Wall # -Wformat=2 -Wpointer-arith -Wbad-function-cast -Wstrict-prototypes -Wmissing-prototypes -Winline -Wdisabled-optimization -Wfloat-equal

all:	$(PROGS)

$(PROG1): $(OBJS1)
	$(CC) $(CFLAGS) $(LDFLAGS) $^ $(LDLIBS) -o $@

clean:
	rm -f $(PROGS) *.o *.eap lib/* include/*