# $FreeBSD$

PORTNAME=	zathura-cb
PORTVERSION=	0.1.4
PORTREVISION=	1
CATEGORIES=	graphics
MASTER_SITES=	http://pwmt.org/projects/zathura-cb/download/

MAINTAINER=	mike.d.ft402@gmail.com
COMMENT=	Comic book plugin for Zathura PDF viewer

LICENSE=	zlib
LICENSE_NAME=	zlib license
LICENSE_FILE=	${WRKSRC}/LICENSE
LICENSE_PERMS=	dist-mirror pkg-mirror auto-accept

LIB_DEPENDS=	libarchive.so:${PORTSDIR}/archivers/libarchive
BUILD_DEPENDS=	zathura:${PORTSDIR}/graphics/zathura
RUN_DEPENDS=	zathura:${PORTSDIR}/graphics/zathura

PLIST_FILES=	lib/zathura/cb.so share/applications/zathura-cb.desktop

USES=		desktop-file-utils gmake pkgconfig
USE_GNOME=	glib20 gtk30
USE_OPENSSL=	yes

post-install:
	${STRIP_CMD} ${STAGEDIR}${LOCALBASE}/lib/zathura/cb.so

.include <bsd.port.mk>
