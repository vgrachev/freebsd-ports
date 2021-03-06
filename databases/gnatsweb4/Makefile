# Created by: Oliver Eikemeier <eikemeier@fillmore-labs.com>
# $FreeBSD$

PORTNAME=	gnatsweb
PORTVERSION=	4.00
PORTREVISION=	4
CATEGORIES=	databases devel www
MASTER_SITES=	GNU

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Gnatsweb, a GNATS web interface

LICENSE=	GPLv2 # or later
LICENSE_FILE=	${WRKSRC}/COPYING

RUN_DEPENDS=	p5-MIME-Base64>=0:${PORTSDIR}/converters/p5-MIME-Base64

USE_APACHE_RUN=	22+

USES=		perl5
USE_PERL5=	run
NO_BUILD=	yes

CGI_DIR?=	${WWWDIR}/cgi-bin

PLIST_SUB=	CGI_DIR="${CGI_DIR:S,^${PREFIX}/,,}"

PORTDOCS=	CUSTOMIZE CUSTOMIZE.cb CUSTOMIZE.vars \
		ChangeLog INSTALL NEWS README TROUBLESHOOTING

PORTEXAMPLES=	gnatsweb-site-example.pl

OPTIONS_DEFINE=	DOCS EXAMPLES

do-install:
	@${MKDIR} ${STAGEDIR}${ETCDIR} ${STAGEDIR}${CGI_DIR} \
		${STAGEDIR}${DOCSDIR} ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/gnatsweb-site.pl \
		${STAGEDIR}${ETCDIR}/gnatsweb-site.pl.sample
	${INSTALL_SCRIPT} ${WRKSRC}/gnatsweb.pl ${STAGEDIR}${CGI_DIR}
	${LN} -s  ${ETCDIR}/gnatsweb-site.pl ${STAGEDIR}${CGI_DIR}
	${INSTALL_DATA} ${WRKSRC}/gnatsweb.html ${STAGEDIR}${CGI_DIR}
	for doc in ${PORTDOCS}; do \
		${INSTALL_DATA} ${WRKSRC}/$${doc} ${STAGEDIR}${DOCSDIR}; \
	done
	for example in ${PORTEXAMPLES}; do \
		${INSTALL_DATA} ${WRKSRC}/$${example} \
			${STAGEDIR}${EXAMPLESDIR}; \
	done

.include <bsd.port.mk>
