# Created by: Ashish SHUKLA <ashish@FreeBSD.org>
# $FreeBSD$

PORTNAME=	libasr
PORTVERSION=	1.0.1
PORTREVISION=	1
CATEGORIES=	dns
MASTER_SITES=	http://www.opensmtpd.org/archives/ \
		http://distfiles.pirateparty.in/ashish/

MAINTAINER=	ashish@FreeBSD.org
COMMENT=	Asynchronous DNS resolver library

LICENSE=	ISCL BSD4CLAUSE BSD3CLAUSE BSD2CLAUSE
LICENSE_COMB=	multi
LICENSE_FILE=	${WRKSRC}/LICENCE

CONFLICTS=	libasr-devel-[0-9]*
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip

USES=		libtool
USE_LDCONFIG=	yes

.include <bsd.port.mk>
