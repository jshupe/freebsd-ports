# Created by: gahr
# $FreeBSD$

PORTNAME=	csoap
PORTVERSION=	1.1.0
PORTREVISION=	2
CATEGORIES=	devel net www
MASTER_SITES=	SF/${PORTNAME}/libsoap/${PORTVERSION}
DISTNAME=	libsoap-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Client/server SOAP library written in pure C

GNU_CONFIGURE=	yes
USES=		pathfix libtool
USE_GNOME=	libxml2
USE_LDCONFIG=	yes

WRKSRC=		${WRKDIR}/libsoap-${PORTVERSION}

.include <bsd.port.mk>
