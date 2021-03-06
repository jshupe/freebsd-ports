# $FreeBSD$

PORTNAME=	reviewboard
PORTVERSION=	1.7.22
CATEGORIES=	www devel
MASTER_SITES=	http://downloads.reviewboard.org/releases/ReviewBoard/${PORTVERSION:R}/
DISTNAME=	ReviewBoard-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Web-based code review tool

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/COPYING

RUN_DEPENDS=	python:${PORTSDIR}/lang/python \
		${PYTHON_PKGNAMEPREFIX}django14>=1.4.3:${PORTSDIR}/www/py-django14 \
		${PYTHON_PKGNAMEPREFIX}django-evolution>=0.6.7:${PORTSDIR}/www/py-django-evolution \
		${PYTHON_PKGNAMEPREFIX}django-pipeline12>=1.2.24:${PORTSDIR}/www/py-django-pipeline12 \
		${PYTHON_PKGNAMEPREFIX}djblets>=0.7.9:${PORTSDIR}/www/py-djblets \
		${PYTHON_PKGNAMEPREFIX}docutils>0:${PORTSDIR}/textproc/py-docutils \
		${PYTHON_PKGNAMEPREFIX}flup>0:${PORTSDIR}/www/py-flup \
		${PYTHON_PKGNAMEPREFIX}dateutil>=1.5:${PORTSDIR}/devel/py-dateutil \
		${PYTHON_PKGNAMEPREFIX}markdown>=2.2.1:${PORTSDIR}/textproc/py-markdown \
		${PYTHON_PKGNAMEPREFIX}memcached>0:${PORTSDIR}/databases/py-memcached \
		${PYTHON_PKGNAMEPREFIX}mimeparse>=0.1.3:${PORTSDIR}/devel/py-mimeparse \
		${PYTHON_PKGNAMEPREFIX}paramiko>=1.9.0:${PORTSDIR}/security/py-paramiko \
		${PYTHON_PKGNAMEPREFIX}pygments>=1.5:${PORTSDIR}/textproc/py-pygments \
		${PYTHON_PKGNAMEPREFIX}pytz>0:${PORTSDIR}/devel/py-pytz \
		${PYTHON_PKGNAMEPREFIX}recaptcha>0:${PORTSDIR}/www/py-recaptcha \
		${PYTHON_PKGNAMEPREFIX}futures>=0:${PORTSDIR}/devel/py-futures \
		${PYTHON_PKGNAMEPREFIX}mimeparse>=0.1.3:${PORTSDIR}/devel/py-mimeparse
BUILD_DEPENDS=	python:${PORTSDIR}/lang/python \
		${PYTHON_PKGNAMEPREFIX}django14>=1.4.3:${PORTSDIR}/www/py-django14 \
		${PYTHON_PKGNAMEPREFIX}django-evolution>=0.6.7:${PORTSDIR}/www/py-django-evolution \
		${PYTHON_PKGNAMEPREFIX}djblets>=0.7.7:${PORTSDIR}/www/py-djblets \
		${PYTHON_PKGNAMEPREFIX}futures>=0:${PORTSDIR}/devel/py-futures \
		${PYTHON_PKGNAMEPREFIX}jsmin>0:${PORTSDIR}/devel/py-jsmin \
		uglifyjs:${PORTSDIR}/www/uglifyjs

USES=		python:2
USE_PYTHON=	distutils
PYDISTUTILS_PKGNAME=	ReviewBoard
# avoid leftover /root/.subversion
MAKE_ENV+=		HOME=${WRKDIR}

OPTIONS_DEFINE=	SVN
OPTIONS_DEFAULT=	SVN

SVN_DESC=	Support reviews for SVN repository

SVN_RUN_DEPENDS=	pysvn>0:${PORTSDIR}/devel/pysvn

post-patch:
	@${REINPLACE_CMD} -e  "s|TIME_ZONE = 'UTC'|TIME_ZONE = 'Etc/UTC'|" ${WRKSRC}/reviewboard/settings.py
	@${REINPLACE_CMD} -e 's|python-dateutil==1.5|python-dateutil|' ${WRKSRC}/setup.py
	@${FIND} ${WRKSRC} -name '*.bak' -delete

.include <bsd.port.mk>
