# Created by: Tom McLaughlin <tmclaugh@sdf.lonestar.org>
# $FreeBSD$

# Port logic gratuitously stolen from x11-themes/kde-icons-noia by
# lioux@.  If it's not defined here and you think it should be, check
# x11-themes/gnome-icons/bsd.gnome-icons.mk for it.

PORTNAME=	aqua-fusion
PORTVERSION=	20030216
PORTREVISION=	3
CATEGORIES=	x11-themes gnome
MASTER_SITES=	GNOME/teams/art.gnome.org/archive/themes/icon
DISTNAME=	ICON-AquaFusion

MAINTAINER=	ports@FreeBSD.org
COMMENT=	AquaFusion Icons for Gnome

RESTRICTED=	${REASON}

USES=	tar:bzip2
WRKSRC=		"${WRKDIR}/AquaFusion"

.include "${.CURDIR}/../gnome-icons/bsd.gnome-icons.mk"
.include <bsd.port.mk>
