# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Tie-LevelDB
PORTVERSION=	0.07
PORTREVISION=	3
CATEGORIES=	databases perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Perl Interface to the Google LevelDB NoSQL database

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

LIB_DEPENDS=	libleveldb.so:${PORTSDIR}/databases/leveldb

MAKE_ARGS=	CC="${CXX}"
USE_PERL5=	configure
USES=		compiler gmake perl5

.include <bsd.port.pre.mk>

.if ${COMPILER_TYPE} == clang
CFLAGS+=	-Wno-reserved-user-defined-literal
.endif

post-patch:
	@${REINPLACE_CMD} -e '/build_detect_platform/d' \
		-e 's|build_config.mk|${LOCALBASE}/share/leveldb/&|' \
		-e '/OBJECT/ s|".*\(LevelDB\.o\).*"|"\1"|' \
		-e '/INC/ s|-I|-I${LOCALBASE}/include &|' \
		-e '/LIBS/ s|\[\(.*\)\]|["-L${LOCALBASE}/lib -lleveldb " . (\1)]|' \
		-e 's|g++|${CXX}|' \
			${WRKSRC}/Makefile.PL

.include <bsd.port.post.mk>
