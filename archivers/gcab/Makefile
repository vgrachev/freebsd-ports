# Created by: kwm@FreeBSD.org
# $FreeBSD$

PORTNAME=	gcab
PORTVERSION=	0.5
CATEGORIES=	archivers gnome
MASTER_SITES=	GNOME

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	GObject library to create cabinet files

BUILD_DEPENDS=	vala:${PORTSDIR}/lang/vala

USES=		gettext gmake libtool pathfix pkgconfig tar:xz
GNU_CONFIGURE=	yes
USE_GNOME=	glib20 intlhack introspection:build

.include <bsd.port.mk>
