# Created by: Alexander Brovikov <alexander@brovikov.ru>
# $FreeBSD$

PORTNAME=	libsrtp
DISTVERSIONPREFIX=	v
DISTVERSION=	1.5.2
PORTREVISION=	1
CATEGORIES=	net

MAINTAINER=	alexander@brovikov.ru
COMMENT=	Secure RTP (SRTP) Reference Implementation

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

USE_GITHUB=	yes
GH_ACCOUNT=	cisco

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-openssl
CPPFLAGS+=	-I${OPENSSLBASE}/include
LIBS+=		-L${OPENSSLBASE}/lib
USES=		gmake pathfix pkgconfig
USE_LDCONFIG=	yes
USE_OPENSSL=	yes

.if ! defined(WITH_DEBUG)
CONFIGURE_ARGS+=--disable-debug
.endif

.include <bsd.port.options.mk>

.if ${OPSYS} == FreeBSD && ${OSVERSION} < 1000015
WITH_OPENSSL_PORT=	yes
.endif

post-patch:
	@${REINPLACE_CMD} '/pkg-config.*openssl/d' ${WRKSRC}/configure

post-build:
	@(cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} ${MAKE_CMD} ${MAKE_FLAGS} \
		${MAKEFILE} ${MAKE_ARGS} shared_library)

check test runtest regression-test: build
	${SETENV} LD_LIBRARY_PATH=${WRKSRC} ${MAKE_CMD} -C ${WRKSRC} runtest

.include <bsd.port.mk>
