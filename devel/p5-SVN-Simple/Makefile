# Created by: Autrijus Tang <autrijus@autrijus.org>
# $FreeBSD$

PORTNAME=	SVN-Simple
PORTVERSION=	0.28
PORTREVISION=	3
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Simple interface to SVN::Delta::Editor

BUILD_DEPENDS=	p5-subversion>=0:${PORTSDIR}/devel/p5-subversion
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

regression-test:
	cd ${WRKSRC} && ${MAKE} test

.include <bsd.port.pre.mk>

.if ${ARCH} == "powerpc"
BROKEN=		Does not configure on powerpc
.endif

.include <bsd.port.post.mk>
