# $FreeBSD$

PORTNAME=	sensu-plugin
DISTVERSION=	4.0.0
PORTREVISION=	1
CATEGORIES=	sysutils rubygems
MASTER_SITES=	RG

MAINTAINER=	y@trombik.org
COMMENT=	Framework for writing Sensu plugins & handlers with Ruby

LICENSE=	MIT

RUN_DEPENDS=    rubygem-json>0:devel/rubygem-json \
    rubygem-mixlib-cli>=1.5:devel/rubygem-mixlib-cli

USES=		gem
USE_RUBY=	yes

PLIST_FILES= bin/mutator-sensu-go-into-ruby.rb

post-patch:
	${REINPLACE_CMD} -e 's|%%PREFIX%%|${PREFIX}|g' ${WRKSRC}/lib/sensu-plugin/utils.rb
    ${RM} ${WRKSRC}/lib/sensu-plugin/utils.rb.bak

.include <bsd.port.mk>
