# Created by: Alexander Botero-Lowry <alexbl@FreeBSD.org>
# $FreeBSD$

PORTNAME=	event-loop
PORTVERSION=	0.3
CATEGORIES=	devel ruby
MASTER_SITES=	http://www.brockman.se/software/ruby-event-loop/
PKGNAMEPREFIX=	${RUBY_PKGNAMEPREFIX}

MAINTAINER=	ruby@FreeBSD.org
COMMENT=	Event loop for Ruby

USE_RUBY=	yes
USE_RAKE=	yes

do-configure:
	@cd ${WRKSRC} && ${RUBY} setup.rb config --prefix=${PREFIX}

do-build:
	@cd ${WRKSRC} && ${RUBY} setup.rb setup

do-install:
	@cd ${WRKSRC} && ${RUBY} setup.rb install --prefix=${STAGEDIR}

.include <bsd.port.pre.mk>

.if ${RUBY_VER} >= 2.2
BROKEN=		Does not build
.endif

.include <bsd.port.post.mk>
