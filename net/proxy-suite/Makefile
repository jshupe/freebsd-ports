# Created by: Thomas Quinot <thomas@cuivre.fr.eu.org>
# $FreeBSD$

PORTNAME=	proxy-suite
PORTVERSION=	1.9.2.4
PORTREVISION=	3
CATEGORIES=	net
MASTER_SITES=	ftp://ftp.suse.com/pub/projects/proxy-suite/src/

MAINTAINER=	thomas@FreeBSD.org
COMMENT=	The SuSE Proxy-Suite, a set of programs to enhance firewall security
LICENSE=	GPLv2

USE_AUTOTOOLS=	autoconf
USES=		gmake tar:bzip2

#
# basic configure args
#
CPPFLAGS+=	-I${LOCALBASE}/include
CONFIGURE_ARGS=	--prefix=${PREFIX} --with-libwrap=/usr/lib --with-regex \
		--localstatedir=/var/run \
		--enable-warnings --enable-so-linger \
		--disable-proc-mods

#
# OPTIONAL: RFC1579 support -- not complete yet.
#
.if defined(WITH_RFC1579)
CONFIGURE_ARGS+=	--enable-rfc1579
.endif

#
# OPTIONAL: include ldap-support
#
.if defined(WITH_LDAP)
USE_OPENLDAP=		yes
CONFIGURE_ARGS+=	--with-libldap=${LOCALBASE}/lib
.else
CONFIGURE_ARGS+=	--without-libldap
.endif

#
# OPTIONAL: re-build the sgml documentation (postscript, html)
# unfortunatenly this docu it is not up to date :-((
# reading of the manual pages and HOWTO's makes more sense...
#
.if !defined(WITH_SGMLDOC)
ALL_TARGET=	 -C ftp-proxy
.endif

MAKE_ARGS=	INST_ROOT=${STAGEDIR} CONF_DST=ftp-proxy.conf.sample

SUB_FILES=	pkg-message

.include <bsd.port.pre.mk>

# XXX: newer autoconf's rely on the compiler result, not the preprocessor
#      for checking headers, so the configure.in needs to be fixed upstream
#      to properly include dependencies
post-configure:
	@${ECHO} "#define HAVE_NET_IF_H 1" >> ${WRKSRC}/config.h
	@${ECHO} "#define HAVE_NETINET_IP_H 1" >> ${WRKSRC}/config.h
	@${ECHO} "#define HAVE_NETINET_IP_FIL_H 1" >> ${WRKSRC}/config.h
	@${ECHO} "#define HAVE_NETINET_IP_NAT_H 1" >> ${WRKSRC}/config.h

pre-install:
	@${STRIP_CMD} ${WRKSRC}/ftp-proxy/ftp-proxy

post-install:
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.post.mk>
