# Created by: chinsan <chinsan@mail20000.com.tw>
# $FreeBSD$

PORTNAME=	b2evolution
PORTVERSION=	4.0.5
DISTVERSIONSUFFIX=	-${B2EVO_DATE}
PORTREVISION=	1
CATEGORIES=	www
MASTER_SITES=	SF/evocms/${PORTNAME}/b2evo%20${PORTVERSION}-stable

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Multilingual, multiuser, multi-blog engine

PATCH_DEPENDS=	unzip:${PORTSDIR}/archivers/unzip

USES=		dos2unix zip

B2EVO_DATE?=	stable-2011-03-23
USE_PHP=	mysql pcre session xml
NO_BUILD=	YES
WANT_PHP_WEB=	YES

TMPDIR?=	${PORTNAME}
WRKSRC=		${WRKDIR}/${TMPDIR}
B2EVO_URL?=	b2evo
B2EVO_DIR?=	www/${B2EVO_URL}
PLIST=		${WRKDIR}/pkg-plist
WARNING=	${PKGDIR}/pkg-warning

OPTIONS_DEFINE=	MYSQL
OPTIONS_DEFAULT=	MYSQL

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MMYSQL}
USE_MYSQL=	server
.endif

pre-everything::
	@${SH} ${WARNING}

pre-install:
	@${ECHO_CMD} -e '@owner ${WWWOWN}\n@group ${WWWGRP}' > ${PLIST}
	@cd ${WRKSRC} && ${FIND} -s . -type f | \
		${SED} -e 's|^./||;s|^|${B2EVO_DIR}/|' >> ${PLIST} \
		&& ${FIND} -d * -type d | \
		${SED} -e 's|^|@dirrm ${B2EVO_DIR}/|' >> ${PLIST} \
		&& ${ECHO_CMD} @dirrm ${B2EVO_DIR} >> ${PLIST}
	@${ECHO_CMD} -e '@owner root\n@group wheel' >> ${PLIST}

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${B2EVO_DIR}
	@${CHMOD} 755 ${STAGEDIR}${PREFIX}/${B2EVO_DIR}
	@${CP} -R ${WRKSRC}/ ${STAGEDIR}${PREFIX}/${B2EVO_DIR}
	@${CHMOD} 665 ${STAGEDIR}${PREFIX}/${B2EVO_DIR}/blogs/conf/_config.php

post-install:
	@${SED} -e 's|%%PREFIX%%|${PREFIX}|' \
		-e 's|%%B2EVO_DIR%%|${B2EVO_DIR}|; s|%%B2EVO_URL%%|${B2EVO_URL}|' \
		${PKGMESSAGE}

.include <bsd.port.mk>
