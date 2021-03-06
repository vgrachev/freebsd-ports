# Created by: Olivier Duchateau
# $FreeBSD$

PORTNAME=	lollypop
PORTVERSION=	0.9.4
CATEGORIES=	audio
MASTER_SITES=	https://github.com/gnumdk/%SUBDIR%/
MASTER_SITE_SUBDIR=	${PORTNAME}/releases/download/${PORTVERSION}

MAINTAINER=	olivierd@FreeBSD.org
COMMENT=	Play and organize your music collection

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}mutagen>=1.26:${PORTSDIR}/audio/py-mutagen \
	${PYTHON_PKGNAMEPREFIX}sqlite3>=2.7.8:${PORTSDIR}/databases/py-sqlite3 \
	${PYTHON_PKGNAMEPREFIX}dbus>=1.1.1:${PORTSDIR}/devel/py3-dbus
LIB_DEPENDS=	libnotify.so:${PORTSDIR}/devel/libnotify
RUN_DEPENDS=	gnome-icon-theme>=3.6.2:${PORTSDIR}/x11-themes/gnome-icon-theme-symbolic

USES=	shebangfix python:3 pkgconfig gettext gmake tar:xz
GNU_CONFIGURE=	yes
USE_GNOME=	glib20 gtk30 py3gobject3 introspection:build intltool intlhack
USE_SQLITE=	yes
USE_GSTREAMER1=	yes mad ogg flac opus libav
USE_PYTHON=	py3kplist
INSTALLS_ICONS=	yes

SHEBANG_FILES=	src/*.py
SHEBANG_LANG=	python
python_OLD_CMD=	/usr/bin/python
python_CMD=	${PYTHON_CMD}

GLIB_SCHEMAS=	org.gnome.Lollypop.gschema.xml

OPTIONS_DEFINE=	PULSEAUDIO
PULSEAUDIO_USE=	gstreamer1=pulse

SUB_FILES=	pkg-message

.include <bsd.port.pre.mk>

.if defined(PACKAGE_BUILDING) && ${PYTHON_VER} != ${PYTHON_DEFAULT}
IGNORE=	you have python ${PYTHON_DEFAULT} set as the default, and this needs ${PYTHON_VER}
.endif

.include <bsd.port.post.mk>
