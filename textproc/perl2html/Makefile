# Created by: Martin Kammerhofer
# $FreeBSD$

PORTNAME=	perl2html
PORTVERSION=	0.9.2
PORTREVISION=	1
CATEGORIES=	textproc www
MASTER_SITES=	${MASTER_SITE_SUNSITE}
MASTER_SITE_SUBDIR=	apps/www/converters

MAINTAINER=	mkamm@gmx.net
COMMENT=	Perl sources to HTML converter

LICENSE=	GPLv2

GNU_CONFIGURE=	yes
OPTIONS_DEFINE=	DOCS

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${STAGEDIR}${DOCSDIR}
.for file in AUTHORS NEWS README
	${INSTALL_MAN} ${WRKSRC}/${file} ${STAGEDIR}${DOCSDIR}
.endfor
.endif

.include <bsd.port.mk>
