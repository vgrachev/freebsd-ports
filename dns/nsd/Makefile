# Created by: alexis
# $FreeBSD$

PORTNAME=	nsd
PORTVERSION=	4.1.1
CATEGORIES=	dns ipv6
MASTER_SITES=	http://www.nlnetlabs.nl/downloads/nsd/	\
		ftp://ftp.rhnet.is/pub/nsd/

MAINTAINER=	jaap@NLnetLabs.nl
COMMENT=	Authoritative only non-recursive name server

LICENSE=	BSD3CLAUSE

CONFLICTS=	nsd-[0-3]* nsd3-[0-9]*

USE_RC_SUBR=	nsd

NSDUSER?=	nsd
NSDGROUP?=	nsd
NSDLSDIR=	/var
NSDDBDIR=	/var/db/nsd
NSDRUNDIR=	/var/run/nsd
NSDMAX_IPS?=	512

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-libevent=${LOCALBASE} \
		--with-user=${NSDUSER} \
		--with-configdir=${PREFIX}/etc/nsd \
		--localstatedir=${NSDLSDIR} \
		--with-dbfile=${NSDDBDIR}/nsd.db \
		--with-pidfile=${NSDRUNDIR}/nsd.pid

PLIST_SUB=	NSDUSER=${NSDUSER} \
		NSDGROUP=${NSDGROUP} \
		NSDDBDIR=${NSDDBDIR} \
		NSDRUNDIR=${NSDRUNDIR}

USERS=		${NSDUSER}
GROUPS=		${NSDGROUP}

USE_OPENSSL=	yes

PORTDOCS=	CREDITS ChangeLog LICENSE NSD-DATABASE NSD-DIFFFILE \
		NSD-4-features NSD-FOR-BIND-USERS README README.icc RELNOTES \
		REQUIREMENTS TESTPLAN TODO UPGRADING coding-style \
		differences.tex

OPTIONS_DEFINE=		ROOT_SERVER LARGEFILE IPV6 BIND8_STATS CHECKING \
		MINRESPSIZE NSEC3 MMAP MAXIPS DOCS RRL ZONE_STATS
OPTIONS_DEFAULT=	LARGEFILE IPV6 NSEC3 MINRESPSIZE RRL

ROOT_SERVER_DESC=	Configure as a root server
LARGEFILE_DESC=		Largefile support
BIND8_STATS_DESC=	BIND8-like NSTATS & XSTATS
CHECKING_DESC=		Internal run-time checks
NSEC3_DESC=		NSEC3 support
MINRESPSIZE_DESC=	Minimial response sizing
MMAP_DESC=		Use mmap instead of malloc (experimental)
MAXIPS_DESC=		Raise max-ips from 8 to ${NSDMAX_IPS}
RRL_DESC=		Response Rate Limiting
ZONE_STATS_DESC=	Separate statistics for each zone

LIB_DEPENDS+=	libevent.so:${PORTSDIR}/devel/libevent2

ROOT_SERVER_CONFIGURE_ENABLE=	root-server
LARGEFILE_CONFIGURE_ENABLE=	largefile
IPV6_CONFIGURE_ENABLE=		ipv6
BIND8_STATS_CONFIGURE_ENABLE=	bind8-stats
CHECKING_CONFIGURE_ENABLE=	checking
NSEC3_CONFIGURE_ENABLE=		nsec3
MINRESPSIZE_CONFIGURE_ENABLE=	minimal-responses
MMAP_CONFIGURE_ENABLE=		mmap
MAXIPS_CONFIGURE_ON=		--with-max-ips=${NSDMAX_IPS}
RRL_CONFIGURE_ENABLE=		ratelimit
ZONE_STATS_CONFIGURE_ENABLE=	zone-stats

post-install:
	${INSTALL_DATA} ${WRKSRC}/nsd.conf.sample \
		${STAGEDIR}${PREFIX}/etc/nsd/nsd.conf.sample
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S|^|${WRKSRC}/doc/|} ${STAGEDIR}${DOCSDIR}
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/sbin/nsd \
		${STAGEDIR}${PREFIX}/sbin/nsd-checkconf \
		${STAGEDIR}${PREFIX}/sbin/nsd-checkzone \
		${STAGEDIR}${PREFIX}/sbin/nsd-control

.include <bsd.port.mk>
