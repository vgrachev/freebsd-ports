# Created by: Douglas K. Rand <rand@meridian-enviro.com>
# $FreeBSD$

PORTNAME=		mapserver
PORTVERSION=		6.4.1
PORTREVISION=		4
CATEGORIES=		graphics www geography
MASTER_SITES=		http://download.osgeo.org/mapserver/

MAINTAINER=		wen@FreeBSD.org
COMMENT=		System for developing web-based GIS applications

LIB_DEPENDS=		libgd.so:${PORTSDIR}/graphics/gd \
			libproj.so:${PORTSDIR}/graphics/proj \
			libpng.so:${PORTSDIR}/graphics/png \
			libjpeg.so:${PORTSDIR}/graphics/jpeg \
			libgif.so:${PORTSDIR}/graphics/giflib

USES=			cmake:outsource
USE_GNOME=		libxml2
LDFLAGS+=		-L${LOCALBASE} -pthread
CMAKE_ARGS+=		-DCMAKE_PREFIX_PATH=${LOCALBASE} \
			-DCMAKE_INSTALL_PREFIX=${PREFIX} \
			-DWITH_GD=1
MAKE_JOBS_UNSAFE=	yes

OPTIONS_DEFINE=		FRIBIDI CURL GDAL GEOS KML POSTGIS PHP PERL PYTHON \
			WMS WFS WCS FASTCGI DEBUG CAIRO CAIRO_SVG \
			CLIENT_WMS CLIENT_WFS
OPTIONS_DEFAULT=	FRIBIDI GDAL GEOS CLIENT_WMS CLIENT_WFS
CAIRO_SVG_DESC=		Cairo SVG parser support
GDAL_DESC=		GDAL library support
FRIBIDI_DESC=		Fribidi library support
KML_DESC=		KML support
WMS_DESC=		WMS Server support
WFS_DESC=		WFS Server support
WCS_DESC=               WCS Server support

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MPYTHON}
USES+=			python:2
BUILD_DEPENDS+=		swig2.0:${PORTSDIR}/devel/swig20
CMAKE_ARGS+=		-DWITH_PYTHON=yes
PLIST_SUB+=		PYTHON=""
MAP_EGG=		MapScript-${PORTVERSION}-${PYTHON_VERSION:S/thon//}
PLIST_SUB+=		MAP_EGG=${MAP_EGG}
.else
PLIST_SUB+=		PYTHON="@comment "
.endif

.if ${PORT_OPTIONS:MCAIRO}
LIB_DEPENDS+=		libcairo.so:${PORTSDIR}/graphics/cairo \
			libexpat.so:${PORTSDIR}/textproc/expat2
CMAKE_ARGS+=		-DWITH_CAIRO=1
.else
CMAKE_ARGS+=		-DWITH_CAIRO=0
.endif

.if ${PORT_OPTIONS:MFRIBIDI}
LIB_DEPENDS+=		libfribidi.so:${PORTSDIR}/converters/fribidi
CMAKE_ARGS+=		-DWITH_FRIBIDI=1
.else
CMAKE_ARGS+=		-DWITH_FRIBIDI=0
.endif

.if ${PORT_OPTIONS:MCAIRO_SVG}
LIB_DEPENDS+=		libcairo.so:${PORTSDIR}/graphics/cairo \
			libsvg-cairo.so:${PORTSDIR}/graphics/libsvg-cairo \
			libexpat.so:${PORTSDIR}/textproc/expat2
CMAKE_ARGS+=		-DWITH_SVGCAIRO=1 -DWITH_CAIRO=1
USES+=			pkgconfig
.else
CMAKE_ARGS+=		-DWITH_SVGCAIRO=0
.endif

.if ${PORT_OPTIONS:MKML}
LIB_DEPENDS+=		libxml2.so:${PORTSDIR}/textproc/libxml2
CMAKE_ARGS+=		-DWITH_KML=1
.else
CMAKE_ARGS+=		-DWITH_KML=0
.endif

.if ${PORT_OPTIONS:MWMS}
CMAKE_ARGS+=		-DWITH_WMS=1
.else
CMAKE_ARGS+=		-DWITH_WMS=0
.endif

.if ${PORT_OPTIONS:MWFS}
CMAKE_ARGS+=		-DWITH_WFS=1
.else
CMAKE_ARGS+=		-DWITH_WFS=0
.endif

.if ${PORT_OPTIONS:MWCS}
CMAKE_ARGS+=		-DWITH_WCS=1
.else
CMAKE_ARGS+=		-DWITH_WCS=0
.endif

.if ${PORT_OPTIONS:MGDAL}
USES+=			iconv
LIB_DEPENDS+=		libgdal.so:${PORTSDIR}/graphics/gdal
CMAKE_ARGS+=		-DWITH_GDAL=1
.else
CMAKE_ARGS+=		-DWITH_GDAL=0
.endif

.if ${PORT_OPTIONS:MGEOS}
LIB_DEPENDS+=		libgeos.so:${PORTSDIR}/graphics/geos
CMAKE_ARGS+=		-DWITH_GEOS=1
.else
CMAKE_ARGS+=		-DWITH_GEOS=0
.endif

.if ${PORT_OPTIONS:MPOSTGIS}
USES+=			pgsql
CMAKE_ARGS+=		-DWITH_POSTGIS=1
.else
CMAKE_ARGS+=		-DWITH_POSTGIS=0
.endif

.if ${PORT_OPTIONS:MPHP}
BUILD_DEPENDS+=		${LOCALBASE}/bin/php-config:${PORTSDIR}/lang/php5
RUN_BUILDS+=		${LOCALBASE}/bin/php-config:${PORTSDIR}/lang/php5
PHP_EXTENSION_DIR!=	${LOCALBASE}/bin/php-config --extension-dir | ${SED} -e "s,/usr/local/,,"
CMAKE_ARGS+=		-DWITH_PHP=1
PLIST_SUB+=		PHP_EXTENSION_DIR=${PHP_EXTENSION_DIR}
PLIST_SUB+=		PHP=""
.else
CMAKE_ARGS+=		-DWITH_PHP=0
PLIST_SUB+=		PHP="@comment "
.endif

.if ${PORT_OPTIONS:MPERL}
USES+=		perl5
BUILD_DEPENDS=	${LOCALBASE}/bin/swig2.0:${PORTSDIR}/devel/swig20
CMAKE_ARGS+=	-DWITH_PERL=1
PLIST_SUB+=	PERL=""
.else
CMAKE_ARGS+=	-DWITH_PERL=0
PLIST_SUB+=	PERL="@comment "
.endif

.if ${PORT_OPTIONS:MCURL}
LIB_DEPENDS+=		libcurl.so:${PORTSDIR}/ftp/curl
CMAKE_ARGS+=		-DWITH_CURL=1
.else
CMAKE_ARGS+=		-DWITH_CURL=0
.endif

.if ${PORT_OPTIONS:MFASTCGI}
BUILD_DEPENDS+=		${LOCALBASE}/bin/cgi-fcgi:${PORTSDIR}/www/fcgi
CMAKE_ARGS+=		-DWITH_FCGI=1
.else
CMAKE_ARGS+=		-DWITH_FCGI=0
.endif

.if ${PORT_OPTIONS:MDEBUG}
CMAKE_ARGS+=		-DCMAKE_BUILD_TYPE=Debug
.else
CMAKE_ARGS+=		-DCMAKE_BUILD_TYPE=Release
.endif

PROG_FILES=		legend scalebar shp2img shptree shptreetst shptreevis \
			sortshp msencrypt tile4ms mapserv

.if ${PORT_OPTIONS:MCLIENT_WMS}
LIB_DEPENDS+=		libcurl.so:${PORTSDIR}/ftp/curl
LIB_DEPENDS+=		libgdal.so:${PORTSDIR}/graphics/gdal
CMAKE_ARGS+=		-DWITH_CURL=1 -DWITH_GDAL=1 -DWITH_CLIENT_WMS=1
.endif

.if ${PORT_OPTIONS:MCLIENT_WFS}
LIB_DEPENDS+=		libcurl.so:${PORTSDIR}/ftp/curl
LIB_DEPENDS+=		libgdal.so:${PORTSDIR}/graphics/gdal
CMAKE_ARGS+=		-DWITH_CURL=1 -DWITH_GDAL=1 -DWITH_CLIENT_WFS=1
.endif

do-install:
.for f in ${PROG_FILES}
	${STRIP_CMD} ${BUILD_WRKSRC}/${f}
	${INSTALL_SCRIPT} ${BUILD_WRKSRC}/${f} ${STAGEDIR}${PREFIX}/bin
.endfor
	${INSTALL_PROGRAM} ${BUILD_WRKSRC}/libmapserver.so.${PORTVERSION} ${STAGEDIR}${PREFIX}/lib

.if ${PORT_OPTIONS:MPHP}
	@${MKDIR} ${STAGEDIR}${PREFIX}/${PHP_EXTENSION_DIR}
	${INSTALL_PROGRAM} ${BUILD_WRKSRC}/mapscript/php/php_mapscript.so \
		${STAGEDIR}${PREFIX}/${PHP_EXTENSION_DIR}/
.endif

.if ${PORT_OPTIONS:MPYTHON}
	@${MKDIR} ${STAGEDIR}${PYTHON_SITELIBDIR}/
	(cd ${BUILD_WRKSRC}/mapscript/python && ${CP} mapscript.py _mapscript.so ${STAGEDIR}${PYTHON_SITELIBDIR}/)
.endif

post-install:
	@${LN} -s ${PREFIX}/lib/libmapserver.so.6.4.1 ${STAGEDIR}${PREFIX}/lib/libmapserver.so.1
	@${LN} -s ${PREFIX}/lib/libmapserver.so.1 ${STAGEDIR}${PREFIX}/lib/libmapserver.so

.if ${PORT_OPTIONS:MPHP}
	@${ECHO_MSG} "Please add the line extension=php_mapscript.so to ${PREFIX}/etc/php/extensions.ini"
.endif

.include <bsd.port.mk>
