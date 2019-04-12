# COPYRIGHT AND DISCLAIMER
# 
# Copyright (C) 1996-1997 by the Regents of the University of California.
# Copyright (c) 1999 by the University of Southern California
#
# IN NO EVENT SHALL THE AUTHORS OR DISTRIBUTORS BE LIABLE TO ANY PARTY FOR
# DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES ARISING OUT
# OF THE USE OF THIS SOFTWARE, ITS DOCUMENTATION, OR ANY DERIVATIVES THEREOF,
# EVEN IF THE AUTHORS HAVE BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
# 
# THE AUTHORS AND DISTRIBUTORS SPECIFICALLY DISCLAIM ANY WARRANTIES,
# INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE, AND NON-INFRINGEMENT. THIS SOFTWARE IS
# PROVIDED ON AN "AS IS" BASIS, AND THE AUTHORS AND DISTRIBUTORS HAVE NO
# OBLIGATION TO PROVIDE MAINTENANCE, SUPPORT, UPDATES, ENHANCEMENTS, OR
# MODIFICATIONS.
#
# Taken from the UCB Home-IP trace by Steve Gribble <gribble@cs.berkeley.edu>
#
# $Header: /cvsroot/nsnam/ns-2/indep-utils/webtrace-conv/ucb/Makefile.in,v 1.5 2014/12/17 04:42:00 tom_henderson Exp $

# Top level hierarchy
prefix  = /usr/local
# Pathname of directory to install the binary
BINDEST = /usr/local/bin

CC = g++
MKDEP	= ../../../conf/mkdep

INCLUDE = -I. -I/home/christen/build/ns-allinone-2.36.rc1/tclcl-1.20 -I/home/christen/build/ns-allinone-2.36.rc1/otcl-1.14 -I/home/christen/build/ns-allinone-2.36.rc1/include -I/home/christen/build/ns-allinone-2.36.rc1/include -I/home/christen/build/ns-allinone-2.36.rc1/include -I/usr/include/pcap
CFLAGS =  -Wall -Wno-write-strings -DCPP_NAMESPACE=@CPP_NAMESPACE@
LDFLAGS =  -Wl,-export-dynamic
LIBS = -L/home/christen/build/ns-allinone-2.36.rc1/lib -ltcl8.5  -lnsl -ldl -lm 
INSTALL = /usr/bin/install -c

SRC = tr-stat.cc logparse.cc utils.cc
OBJ = $(SRC:.cc=.o)

all: ucb-tr-stat

ucb-tr-stat: $(OBJ)
	$(CC) $(LDFLAGS) $(CFLAGS) -o $@ $(OBJ) $(LIBS)

install: ucb-tr-stat
	$(INSTALL) -m 555 -o bin -g bin ucb-tr-stat $(DESTDIR)$(BINDEST)

.SUFFIXES: .cc

.cc.o: 
	@rm -f $@
	$(CC) -c $(CFLAGS) $(INCLUDE) -o $@ $*.cc

clean:
	-/bin/rm -f *.o *~ ucb-tr-stat *core

FORCE:
	;

depend: $(SRC)
	$(MKDEP) $(CFLAGS) $(INCLUDE) $(SRC)
