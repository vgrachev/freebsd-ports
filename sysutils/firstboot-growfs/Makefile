# $FreeBSD$

PORTNAME=	firstboot-growfs
PORTVERSION=	1.0
CATEGORIES=	sysutils
MASTER_SITES=	# none
DISTFILES=	# none

MAINTAINER=	swills@FreeBSD.org
COMMENT=	Expand / when the system first boots

NO_WRKSUBDIR=	yes
NO_BUILD=	yes

USE_RC_SUBR=	firstboot_growfs

.include <bsd.port.pre.mk>

.if ${OSVERSION} < 902504 || ( ${OSVERSION} >= 1000000 && ${OSVERSION} < 1000100 ) || ( ${OSVERSION} >= 1000500 && ${OSVERSION} < 1000501 ) || (${OSVERSION} >= 1100000 && ${OSVERSION} < 1100001 )
IGNORE=	first boot rc.d scripts not supported on this version of FreeBSD
.endif

do-fetch do-install:
	@${DO_NADA}

.include <bsd.port.post.mk>
