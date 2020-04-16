# $FreeBSD$

PORTREVISION=   0
CATEGORIES= sysutils
PKGNAMESUFFIX?=	-backend

MAINTAINER=		y@trombik.org
COMMENT=		Distributed applications monitoring, backend only

LICENSE=		APACHE20

OPTIONS_SLAVE=  SENSU_BE
MASTERDIR=	${.CURDIR}/../sensu-go

.include "${MASTERDIR}/Makefile"
