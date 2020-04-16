# $FreeBSD$

PORTREVISION=   0
CATEGORIES= sysutils
PKGNAMESUFFIX?=	-agent

MAINTAINER=		y@trombik.org
COMMENT=		Distributed applications monitoring, sensu-agent tools only

LICENSE=		APACHE20

OPTIONS_SLAVE=  SENSU_AGENT
MASTERDIR=	${.CURDIR}/../sensu-go

.include "${MASTERDIR}/Makefile"
