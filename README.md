# Teamgram - Unofficial open source [mtproto](https://core.telegram.org/mtproto) server written in golang
> open source mtproto server implemented in golang with compatible telegram client.

## Introduce
Open source [mtproto](https://core.telegram.org/mtproto) server implementation written in golang, support private deployment.

## Features
- MTProto 2.0
  - Abridged
  - Intermediate
  - Padded intermediate
  - Full
- API Layer: 170
- private chat
- basic group
- contacts

## Architecture
![Architecture](docs/image/architecture-001.png)

## Installing Teamgram 
`Teamgram` relies on open source high-performance components: 

- **mysql5.7**
- [redis](https://redis.io/)
- [etcd](https://etcd.io/)
- [kafka](https://kafka.apache.org/quickstart)
- [minio](https://docs.min.io/docs/minio-quickstart-guide.html#GNU/Linux)
- [ffmpeg](https://www.johnvansickle.com/ffmpeg/)

Privatization deployment Before `Teamgram`, please make sure that the above five components have been installed. If your server does not have the above components, you must first install Missing components. 

If you have the above components, it is recommended to use them directly. If not, it is recommended to use `docker-compose-env.yaml`.


### Source code deployment
#### Install [Go environment](https://go.dev/doc/install). Make sure Go version is at least 1.17.


#### Get source code　

```
git clone https://github.com/teamgram/teamgram-server.git
cd teamgram-server
```

#### Init data
- init database

	```
	1. create database teamgram
	2. init teamgram database
	   mysql -uroot teamgram < teamgramd/sql/1_teamgram.sql
	   mysql -uroot teamgram < teamgramd/sql/migrate-*.sql
  	   mysql -uroot teamgram < teamgramd/sql/z_init.sql
	```

- init minio buckets
	- bucket names
	  - `documents`
	  - `encryptedfiles`
	  - `photos`
	  - `videos`
	- Access `http://ip:xxxxx` and create


#### Build
	
```
make
```

#### Run

```
cd teamgramd/bin
./runall2.sh
```

### Docker deployment
#### Install [Docker](https://docs.docker.com/get-docker/)

#### Install [Docker Compose](https://docs.docker.com/compose/install/)

#### Get source code

```
git clone https://github.com/teamgram/teamgram-server.git
cd teamgram-server
```

#### Run

```  
# run dependency
docker-compose -f ./docker-compose-env.yaml up -d

# run docker-compose
docker-compose up -d
```
	
## Compatible clients

[Android client for Teamgram](clients/teamgram-android.md)

[iOS client for Teamgram](clients/teamgram-ios.md)

[tdesktop for Teamgram](clients/teamgram-tdesktop.md)



## Give a Star! ⭐

If you like or are using this project to learn or start your solution, please give it a star. Thanks!
