# Created by: Antonio Carlos Venancio Junior (<antonio@inf.ufsc.br>)
# $FreeBSD$

PORTNAME=	radius
PORTVERSION=	1.2.7
CATEGORIES=	net security pear
MASTER_SITES=	http://pecl.php.net/get/
PKGNAMEPREFIX=	pecl-
DIST_SUBDIR=	PECL

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Radius client library for PHP

LICENSE=	BSD3CLAUSE

USES=		tar:tgz
USE_PHP=	yes
USE_PHPEXT=	yes

CONFIGURE_ARGS=	--enable-radius

post-install:
	${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/examples/* ${STAGEDIR}${EXAMPLESDIR}

.include <bsd.port.mk>
