# Created by: Dmitri Nikulin <setagllib@optusnet.com.au>
# $FreeBSD$

PORTNAME=	stress
PORTVERSION=	1.0.4
CATEGORIES=	sysutils
MASTER_SITES=	http://people.seas.harvard.edu/~apw/stress/ \
		http://fossies.org/linux/privat/

MAINTAINER=	skreuzer@FreeBSD.org
COMMENT=	Tool to impose load on and stress test Unix-like systems

LICENSE=	GPLv3

GNU_CONFIGURE=	yes

INFO=		stress
PLIST_FILES=	bin/stress man/man1/stress.1.gz

post-patch:
	@${REINPLACE_CMD} -e 's|^\(CFLAGS\ \)=|\1 +=|; s|^\(CFLAGS.*\)-Wall|\1|' \
		${WRKSRC}/src/Makefile.in

.include <bsd.port.mk>
