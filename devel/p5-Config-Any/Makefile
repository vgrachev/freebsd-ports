# Created by: Lars Balker Rasmussen <lbr@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Config-Any
PORTVERSION=	0.24
PORTREVISION=	3
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Load class configuration data from a number of file formats

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-Config-General>=2.47:${PORTSDIR}/devel/p5-Config-General
RUN_DEPENDS:=	${BUILD_DEPENDS}

OPTIONS_DEFINE=	INI JSON XML YAML
OPTIONS_DEFAULT=INI JSON XML YAML

USES=		perl5
USE_PERL5=	configure

INI_BUILD_DEPENDS=	p5-Config-Tiny>=0:${PORTSDIR}/devel/p5-Config-Tiny
INI_RUN_DEPENDS=	p5-Config-Tiny>=0:${PORTSDIR}/devel/p5-Config-Tiny
JSON_BUILD_DEPENDS=	p5-JSON-XS>=0:${PORTSDIR}/converters/p5-JSON-XS
JSON_RUN_DEPENDS=	p5-JSON-XS>=0:${PORTSDIR}/converters/p5-JSON-XS
XML_BUILD_DEPENDS=	p5-XML-Simple>=0:${PORTSDIR}/textproc/p5-XML-Simple
XML_RUN_DEPENDS=	p5-XML-Simple>=0:${PORTSDIR}/textproc/p5-XML-Simple
YAML_BUILD_DEPENDS=	p5-YAML-LibYAML>=0:${PORTSDIR}/textproc/p5-YAML-LibYAML
YAML_RUN_DEPENDS=	p5-YAML-LibYAML>=0:${PORTSDIR}/textproc/p5-YAML-LibYAML

.include <bsd.port.pre.mk>

.if ${PERL_LEVEL} >= 502000
# Module::Pluggable was first released with perl v5.8.9 and removed from v5.19.0
BUILD_DEPENDS+=	p5-Module-Pluggable>=0:${PORTSDIR}/devel/p5-Module-Pluggable
RUN_DEPENDS+=	p5-Module-Pluggable>=0:${PORTSDIR}/devel/p5-Module-Pluggable
.endif

.include <bsd.port.post.mk>
