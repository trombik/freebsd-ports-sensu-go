PORTNAME?=		sensu-go
PORTVERSION=		6.4.2
CATEGORIES=		sysutils

MAINTAINER=		jp+ports@supplntr.io
COMMENT=		#

LICENSE=		APACHE20

ONLY_FOR_ARCHS=		amd64 i386
BUILD_DEPENDS=		bash:shells/bash

USES=			go:modules
USE_GITHUB=		yes
GH_PROJECT=		sensu-go
GH_ACCOUNT=		sensu
GH_TAGNAME=		v${PORTVERSION}

GO_PKGNAME=		github.com/${GH_ACCOUNT}/${GH_PROJECT}

GO_TARGET=	${SENSU_GO_TARGET}

.if defined(SENSU_AGENT)
SENSU_GO_TARGET=	./cmd/sensu-agent
CONFLICTS=	sensu-go-[0-9]+
COMMENT=		Sensu open source monitoring tool (agent)
PLIST_SUB+=	SENSU_AGENT="" SENSU_BE="@comment " SENSU_CLI="@comment "
.elif defined(SENSU_CLI)
SENSU_GO_TARGET=	./cmd/sensuctl
CONFLICTS=	sensu-go-[0-9]+
COMMENT=		Sensu open source monitoring tool (cli)
PLIST_SUB+=	SENSU_AGENT="@comment " SENSU_BE="@comment " SENSU_CLI=""
.elif defined(SENSU_BE)
SENSU_GO_TARGET=	./cmd/sensu-backend
CONFLICTS=	sensu-go-[0-9]+
COMMENT=		Sensu open source monitoring tool (backend)
PLIST_SUB+=	SENSU_AGENT="@comment " SENSU_BE="" SENSU_CLI="@comment "
.else
SENSU_GO_TARGET=	./cmd/sensu-backend ./cmd/sensu-agent ./cmd/sensuctl
CONFLICTS=	sensu-go-backend-* sensu-go-agent-* sensu-go-cli-*
COMMENT=		Sensu open source monitoring tool (backend, agent, and cli)
PLIST_SUB+=	SENSU_AGENT="" SENSU_BE="" SENSU_CLI=""
SENSU_AGENT=	yes
SENSU_CLI=	yes
SENSU_BE=	yes
.endif

SENSU_VERSION_FLAGS=	-ldflags '-X "github.com/sensu/sensu-go/version.Version=${PORTVERSION}"'
GO_BUILDFLAGS=	${SENSU_VERSION_FLAGS}

GH_TUPLE=	\
		AlecAivazis:survey:v1.4.0:alecaivazis_survey/vendor/gopkg.in/AlecAivazis/survey.v1 \
		AlecAivazis:survey:v1.4.1:alecaivazis_survey_1/vendor/github.com/AlecAivazis/survey \
		Azure:go-ansiterm:d6e3b3328b78:azure_go_ansiterm/vendor/github.com/Azure/go-ansiterm \
		StackExchange:wmi:b12b22c5341f:stackexchange_wmi/vendor/github.com/StackExchange/wmi \
		andybalholm:brotli:v1.0.0:andybalholm_brotli/vendor/github.com/andybalholm/brotli \
		ash2k:stager:6e9c7b0eacd4:ash2k_stager/vendor/github.com/ash2k/stager \
		atlassian:gostatsd:af796620006e:atlassian_gostatsd/vendor/github.com/atlassian/gostatsd \
		beorn7:perks:v1.0.1:beorn7_perks/vendor/github.com/beorn7/perks \
		cespare:xxhash:v2.1.1:cespare_xxhash/vendor/github.com/cespare/xxhash/v2 \
		coreos:go-semver:v0.3.0:coreos_go_semver/vendor/github.com/coreos/go-semver \
		coreos:go-systemd:v22.3.2:coreos_go_systemd/vendor/github.com/coreos/go-systemd/v22 \
		dave:jennifer:d8bdbdbee4e1:dave_jennifer/vendor/github.com/dave/jennifer \
		davecgh:go-spew:v1.1.1:davecgh_go_spew/vendor/github.com/davecgh/go-spew \
		dgrijalva:jwt-go:v3.2.0:dgrijalva_jwt_go/vendor/github.com/dgrijalva/jwt-go \
		dsnet:compress:v0.0.1:dsnet_compress/vendor/github.com/dsnet/compress \
		dustin:go-humanize:v1.0.0:dustin_go_humanize/vendor/github.com/dustin/go-humanize \
		echlebek:crock:v1.0.1:echlebek_crock/vendor/github.com/echlebek/crock \
		echlebek:timeproxy:v1.0.0:echlebek_timeproxy/vendor/github.com/echlebek/timeproxy \
		emicklei:proto:v1.1.0:emicklei_proto/vendor/github.com/emicklei/proto \
		etcd-io:bbolt:v1.3.6:etcd_io_bbolt/vendor/go.etcd.io/bbolt \
		evanphx:json-patch:v5.1.0:evanphx_json_patch/vendor/github.com/evanphx/json-patch/v5 \
		form3tech-oss:jwt-go:v3.2.3:form3tech_oss_jwt_go/vendor/github.com/form3tech-oss/jwt-go \
		fsnotify:fsnotify:v1.4.7:fsnotify_fsnotify/vendor/github.com/fsnotify/fsnotify \
		ghodss:yaml:v1.0.0:ghodss_yaml/vendor/github.com/ghodss/yaml \
		go-ini:ini:v1.51.0:go_ini_ini/vendor/gopkg.in/ini.v1 \
		go-ole:go-ole:v1.2.1:go_ole_go_ole/vendor/github.com/go-ole/go-ole \
		go-resty:resty:v2.5.0:go_resty_resty/vendor/github.com/go-resty/resty/v2 \
		go-sourcemap:sourcemap:v1.0.5:go_sourcemap_sourcemap/vendor/gopkg.in/sourcemap.v1 \
		go-yaml:yaml:496545a6307b:go_yaml_yaml/vendor/gopkg.in/yaml.v3 \
		go-yaml:yaml:v2.4.0:go_yaml_yaml_1/vendor/gopkg.in/yaml.v2 \
		gogo:protobuf:v1.3.2:gogo_protobuf/vendor/github.com/gogo/protobuf \
		golang:crypto:7f63de1d35b0:golang_crypto/vendor/golang.org/x/crypto \
		golang:groupcache:41bb18bfe9da:golang_groupcache/vendor/github.com/golang/groupcache \
		golang:net:a5a99cb37ef4:golang_net/vendor/golang.org/x/net \
		golang:protobuf:v1.5.2:golang_protobuf/vendor/github.com/golang/protobuf \
		golang:snappy:v0.0.1:golang_snappy/vendor/github.com/golang/snappy \
		golang:sys:ebe580a85c40:golang_sys/vendor/golang.org/x/sys \
		golang:text:v0.3.5:golang_text/vendor/golang.org/x/text \
		golang:time:f8bda1e9f3ba:golang_time/vendor/golang.org/x/time \
		google:btree:v1.0.1:google_btree/vendor/github.com/google/btree \
		google:go-genproto:f16073e35f0c:google_go_genproto/vendor/google.golang.org/genproto \
		google:uuid:v1.1.2:google_uuid/vendor/github.com/google/uuid \
		gorilla:mux:v1.8.0:gorilla_mux/vendor/github.com/gorilla/mux \
		gorilla:websocket:v1.4.2:gorilla_websocket/vendor/github.com/gorilla/websocket \
		graph-gophers:dataloader:78139374585c:graph_gophers_dataloader/vendor/github.com/graph-gophers/dataloader \
		graphql-go:graphql:2e2b648ecbe4:graphql_go_graphql/vendor/github.com/graphql-go/graphql \
		grpc-ecosystem:go-grpc-middleware:v1.3.0:grpc_ecosystem_go_grpc_middleware/vendor/github.com/grpc-ecosystem/go-grpc-middleware \
		grpc-ecosystem:go-grpc-prometheus:v1.2.0:grpc_ecosystem_go_grpc_prometheus/vendor/github.com/grpc-ecosystem/go-grpc-prometheus \
		grpc-ecosystem:grpc-gateway:v1.16.0:grpc_ecosystem_grpc_gateway/vendor/github.com/grpc-ecosystem/grpc-gateway \
		grpc:grpc-go:v1.38.0:grpc_grpc_go/vendor/google.golang.org/grpc \
		gxed:GoEndian:0f5c6873267e:gxed_goendian/vendor/github.com/gxed/GoEndian \
		gxed:eventfd:80a92cca79a8:gxed_eventfd/vendor/github.com/gxed/eventfd \
		h2non:filetype:v1.0.3:h2non_filetype/vendor/gopkg.in/h2non/filetype.v1 \
		hashicorp:go-version:v1.2.0:hashicorp_go_version/vendor/github.com/hashicorp/go-version \
		hashicorp:hcl:v1.0.0:hashicorp_hcl/vendor/github.com/hashicorp/hcl \
		inconshreveable:mousetrap:v1.0.0:inconshreveable_mousetrap/vendor/github.com/inconshreveable/mousetrap \
		ipfs:go-log:v1.0.4:ipfs_go_log/vendor/github.com/ipfs/go-log \
		ipfs:go-log:v2.0.5:ipfs_go_log_1/vendor/github.com/ipfs/go-log/v2 \
		jbenet:go-reuseport:15a1cd37f050:jbenet_go_reuseport/vendor/github.com/jbenet/go-reuseport \
		jonboulle:clockwork:v0.2.2:jonboulle_clockwork/vendor/github.com/jonboulle/clockwork \
		json-iterator:go:v1.1.11:json_iterator_go/vendor/github.com/json-iterator/go \
		klauspost:compress:v1.9.2:klauspost_compress/vendor/github.com/klauspost/compress \
		klauspost:pgzip:v1.2.1:klauspost_pgzip/vendor/github.com/klauspost/pgzip \
		kubernetes-sigs:yaml:v1.2.0:kubernetes_sigs_yaml/vendor/sigs.k8s.io/yaml \
		libp2p:go-reuseport:15a1cd37f050:libp2p_go_reuseport/vendor/github.com/libp2p/go-reuseport \
		libp2p:go-sockaddr:v0.1.0:libp2p_go_sockaddr/vendor/github.com/libp2p/go-sockaddr \
		magiconair:properties:v1.8.1:magiconair_properties/vendor/github.com/magiconair/properties \
		mattn:go-colorable:v0.1.4:mattn_go_colorable/vendor/github.com/mattn/go-colorable \
		mattn:go-isatty:v0.0.8:mattn_go_isatty/vendor/github.com/mattn/go-isatty \
		mattn:go-runewidth:v0.0.9:mattn_go_runewidth/vendor/github.com/mattn/go-runewidth \
		matttproud:golang_protobuf_extensions:v1.0.1:matttproud_golang_protobuf_extensions/vendor/github.com/matttproud/golang_protobuf_extensions \
		mgutz:ansi:9520e82c474b:mgutz_ansi/vendor/github.com/mgutz/ansi \
		mholt:archiver:44285f7ed244:mholt_archiver/vendor/github.com/mholt/archiver/v3 \
		mitchellh:go-homedir:v1.1.0:mitchellh_go_homedir/vendor/github.com/mitchellh/go-homedir \
		mitchellh:hashstructure:v1.0.0:mitchellh_hashstructure/vendor/github.com/mitchellh/hashstructure \
		mitchellh:mapstructure:v1.1.2:mitchellh_mapstructure/vendor/github.com/mitchellh/mapstructure \
		modern-go:concurrent:bacd9c7ef1dd:modern_go_concurrent/vendor/github.com/modern-go/concurrent \
		modern-go:reflect2:v1.0.1:modern_go_reflect2/vendor/github.com/modern-go/reflect2 \
		natefinch:lumberjack:v2.0.0:natefinch_lumberjack/vendor/gopkg.in/natefinch/lumberjack.v2 \
		nwaples:rardecode:v1.0.0:nwaples_rardecode/vendor/github.com/nwaples/rardecode \
		olekukonko:tablewriter:v0.0.5:olekukonko_tablewriter/vendor/github.com/olekukonko/tablewriter \
		opentracing:opentracing-go:v1.1.0:opentracing_opentracing_go/vendor/github.com/opentracing/opentracing-go \
		pelletier:go-toml:v1.2.0:pelletier_go_toml/vendor/github.com/pelletier/go-toml \
		pierrec:lz4:v3.0.1:pierrec_lz4/vendor/github.com/pierrec/lz4/v3 \
		pkg:errors:v0.9.1:pkg_errors/vendor/github.com/pkg/errors \
		pmezard:go-difflib:v1.0.0:pmezard_go_difflib/vendor/github.com/pmezard/go-difflib \
		prometheus:client_golang:v1.11.0:prometheus_client_golang/vendor/github.com/prometheus/client_golang \
		prometheus:client_model:v0.2.0:prometheus_client_model/vendor/github.com/prometheus/client_model \
		prometheus:common:v0.26.0:prometheus_common/vendor/github.com/prometheus/common \
		prometheus:procfs:v0.6.0:prometheus_procfs/vendor/github.com/prometheus/procfs \
		robertkrimen:otto:c382bd3c16ff:robertkrimen_otto/vendor/github.com/robertkrimen/otto \
		robfig:cron:v1.2.0:robfig_cron/vendor/github.com/robfig/cron \
		robfig:cron:v3.0.1:robfig_cron_1/vendor/github.com/robfig/cron/v3 \
		sensu:lasr:v1.2.1:sensu_lasr/vendor/github.com/sensu/lasr \
		shirou:gopsutil:v3.21.4:shirou_gopsutil/vendor/github.com/shirou/gopsutil \
		sirupsen:logrus:v1.7.0:sirupsen_logrus/vendor/github.com/sirupsen/logrus \
		soheilhy:cmux:v0.1.5:soheilhy_cmux/vendor/github.com/soheilhy/cmux \
		spf13:afero:v1.1.2:spf13_afero/vendor/github.com/spf13/afero \
		spf13:cast:v1.3.0:spf13_cast/vendor/github.com/spf13/cast \
		spf13:cobra:v1.1.3:spf13_cobra/vendor/github.com/spf13/cobra \
		spf13:jwalterweatherman:v1.0.0:spf13_jwalterweatherman/vendor/github.com/spf13/jwalterweatherman \
		spf13:pflag:v1.0.5:spf13_pflag/vendor/github.com/spf13/pflag \
		spf13:viper:v1.7.0:spf13_viper/vendor/github.com/spf13/viper \
		stretchr:objx:v0.2.0:stretchr_objx/vendor/github.com/stretchr/objx \
		stretchr:testify:v1.7.0:stretchr_testify/vendor/github.com/stretchr/testify \
		subosito:gotenv:v1.2.0:subosito_gotenv/vendor/github.com/subosito/gotenv \
		tklauser:go-sysconf:v0.3.6:tklauser_go_sysconf/vendor/github.com/tklauser/go-sysconf \
		tklauser:numcpus:v0.2.2:tklauser_numcpus/vendor/github.com/tklauser/numcpus \
		tmc:grpc-websocket-proxy:e5319fda7802:tmc_grpc_websocket_proxy/vendor/github.com/tmc/grpc-websocket-proxy \
		uber-go:atomic:v1.7.0:uber_go_atomic/vendor/go.uber.org/atomic \
		uber-go:multierr:v1.6.0:uber_go_multierr/vendor/go.uber.org/multierr \
		uber-go:zap:v1.17.0:uber_go_zap/vendor/go.uber.org/zap \
		ulikunitz:xz:v0.5.6:ulikunitz_xz/vendor/github.com/ulikunitz/xz \
		willf:pad:b3d780601022:willf_pad/vendor/github.com/willf/pad \
		xi2:xz:48954b6210f8:xi2_xz/vendor/github.com/xi2/xz \
		xiang90:probing:43a291ad63a2:xiang90_probing/vendor/github.com/xiang90/probing

SENSU_GH_TUPLE_UNKNOWN_MIRRORS=	\
		open-telemetry:opentelemetry-go-contrib:v0.20.0:open_telemetry_opentelemetry_go_contrib/vendor/go.opentelemetry.io/contrib \
		open-telemetry:opentelemetry-go:v0.20.0:open_telemetry_opentelemetry_go/vendor/go.opentelemetry.io/otel \
		open-telemetry:opentelemetry-proto-go:v0.7.0:open_telemetry_opentelemetry_proto_go/vendor/go.opentelemetry.io/proto \
		protocolbuffers:protobuf-go:v1.26.0:protocolbuffers_protobuf_go/vendor/google.golang.org/protobuf

GH_TUPLE+=	${SENSU_GH_TUPLE_UNKNOWN_MIRRORS}

# XXX these are exceptions. gomod-vendor-diff target cannot reliably generates
# tuples.
GH_TUPLE+= moby:moby:cbde00b44273:docker_docker/vendor/github.com/docker/docker \
	etcd-io:etcd:v3.5.0:etcd_io_etcd/vendor/go.etcd.io/etcd

post-patch:
	${MKDIR} ${GO_WRKSRC}/vendor/github.com/docker
	${RM} ${WRKSRC}/vendor/github.com/libp2p/go-reuseport
	${LN} -s ${WRKSRC}/vendor/github.com/jbenet/go-reuseport ${WRKSRC}/vendor/github.com/libp2p/go-reuseport

	${LN} -s ${WRKSRC}/vendor/go.etcd.io/etcd/api        ${WRKSRC}/vendor/go.etcd.io/etcd/api/v3
	${LN} -s ${WRKSRC}/vendor/go.etcd.io/etcd/client/pkg ${WRKSRC}/vendor/go.etcd.io/etcd/client/pkg/v3
	${LN} -s ${WRKSRC}/vendor/go.etcd.io/etcd/server     ${WRKSRC}/vendor/go.etcd.io/etcd/server/v3
	${LN} -s ${WRKSRC}/vendor/go.etcd.io/etcd/pkg        ${WRKSRC}/vendor/go.etcd.io/etcd/pkg/v3
	${LN} -s ${WRKSRC}/vendor/go.etcd.io/etcd/raft       ${WRKSRC}/vendor/go.etcd.io/etcd/raft/v3

	${MKDIR} ${WRKSRC}/vendor/github.com/sensu/sensu-go/api/core
	${LN} -s ${WRKSRC}/api/core/v2 ${WRKSRC}/vendor/github.com/sensu/sensu-go/api/core/v2
	${LN} -s ${WRKSRC}/api/core/v3 ${WRKSRC}/vendor/github.com/sensu/sensu-go/api/core/v3
	${LN} -s ${WRKSRC}/types       ${WRKSRC}/vendor/github.com/sensu/sensu-go/types

post-install:
.if defined(SENSU_AGENT)
	${INSTALL} -d ${STAGEDIR}${PREFIX}/etc/sensu
	${INSTALL_DATA} ${PATCHDIR}/agent.yml.sample \
		${STAGEDIR}${PREFIX}/etc/sensu/agent.yml.sample
.endif
.if defined(SENSU_BE)
	${INSTALL} -d ${STAGEDIR}${PREFIX}/etc/sensu
	${INSTALL_DATA} ${PATCHDIR}/backend.yml.sample \
		${STAGEDIR}${PREFIX}/etc/sensu/backend.yml.sample
.endif

.include <bsd.port.mk>
