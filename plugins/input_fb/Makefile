###############################################################
#
# Purpose: Makefile for "M-JPEG Streamer"
# Author.: Tom Stoeveken (TST)
# Version: 0.3
# License: GPL
#
###############################################################

CC = gcc

OTHER_HEADERS = ../../mjpg_streamer.h ../../utils.h ../output.h ../input.h

CFLAGS += -O1 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -I/opt/vc/include -I/opt/vc/include/interface/vcos/pthreads -I/opt/vc/include/interface/vmcs_host/linux

#CFLAGS += -g
#CFLAGS += -DDEBUG

LFLAGS += -ljpeg -L/opt/vc/lib -lbcm_host

all: input_fb.so

clean:
	rm -f *.a *.o core *~ *.so *.lo

input_fb.so: $(OTHER_HEADERS) input_fb.c jpeg_utils.lo
	$(CC) $(CFLAGS) -o $@ input_fb.c jpeg_utils.lo $(LFLAGS)

jpeg_utils.lo: jpeg_utils.c jpeg_utils.h
	$(CC) -c $(CFLAGS) -o $@ jpeg_utils.c
