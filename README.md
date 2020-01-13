# envoy, mysql, ext_authz 

```
$ docker-compose build
$ docker-compose up -d
$ docker run --rm -it --network envoymesh mysql:5.5 mysql -h envoy -P 1999 -u root
mysql > select * from test;
mysql > \q
$ docker-compose logs ext_authz
... snip ...
ext_authz_1  | 2020/01/13 14:45:43 context.Background.WithDeadline(2020-01-13 14:45:43.20244672 +0000 UTC m=+7.012238031 [199.379735ms]).WithValue(type peer.peerKey, val <not Stringer>).WithValue(type metadata.mdIncomingKey, val <not Stringer>).WithValue(type grpc.streamKey, val <not Stringer>)
ext_authz_1  | 2020/01/13 14:45:43 {"attributes":{"source":{"address":{"socketAddress":{"address":"192.168.224.5","portValue":35110}}},"destination":{"address":{"socketAddress":{"address":"192.168.224.4","portValue":1999}}},"metadataContext":{"filterMetadata":{"envoy.filters.network.mysql_proxy":{}}}}}
ext_authz_1  | 2020/01/13 14:45:43 context.Background.WithDeadline(2020-01-13 14:45:43.205384109 +0000 UTC m=+7.015175423 [199.683771ms]).WithValue(type peer.peerKey, val <not Stringer>).WithValue(type metadata.mdIncomingKey, val <not Stringer>).WithValue(type grpc.streamKey, val <not Stringer>)
ext_authz_1  | 2020/01/13 14:45:43 {"attributes":{"source":{"address":{"socketAddress":{"address":"192.168.224.5","portValue":35110}}},"destination":{"address":{"socketAddress":{"address":"192.168.224.4","portValue":1999}}},"metadataContext":{"filterMetadata":{"envoy.filters.network.mysql_proxy":{}}}}}
ext_authz_1  | 2020/01/13 14:45:54 context.Background.WithDeadline(2020-01-13 14:45:55.148795645 +0000 UTC m=+18.958586985 [199.473448ms]).WithValue(type peer.peerKey, val <not Stringer>).WithValue(type metadata.mdIncomingKey, val <not Stringer>).WithValue(type grpc.streamKey, val <not Stringer>)
ext_authz_1  | 2020/01/13 14:45:54 {"attributes":{"source":{"address":{"socketAddress":{"address":"192.168.224.5","portValue":35110}}},"destination":{"address":{"socketAddress":{"address":"192.168.224.4","portValue":1999}}},"metadataContext":{"filterMetadata":{"envoy.filters.network.mysql_proxy":{"test":["select"]}}}}}
```
