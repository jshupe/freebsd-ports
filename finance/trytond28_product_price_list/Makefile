# Created by: Matthias Petermann <matthias@petermann-it.de>
# $FreeBSD$

PORTNAME=	trytond28_product_price_list
PORTVERSION=	2.8.0
PORTREVISION=	1
CATEGORIES=	finance python
MASTER_SITES=	https://pypi.python.org/packages/source/t/trytond_product_price_list/ \
		http://downloads.tryton.org/${PORTVERSION:R}/
DISTNAME=	trytond_product_price_list-${PORTVERSION}

MAINTAINER=	matthias@petermann-it.de
COMMENT=	Tryton Application Platform (Product Price List Module)

LICENSE=	GPLv3

RUN_DEPENDS=	trytond28_product>=2.8.0:${PORTSDIR}/finance/trytond28_product \
		trytond28_party>=2.8.0:${PORTSDIR}/finance/trytond28_party \
		trytond28_company>=2.8.0:${PORTSDIR}/finance/trytond28_company

CONFLICTS=	trytond_product_price_list-2.[46].*

USES=		python
USE_PYTHON=	distutils autoplist

.include <bsd.port.mk>
