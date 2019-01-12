# Rails Exchange

#### Requeriments:

- docker (version 18.06.1-ce)
- docker-compose (version 1.23.2) 

#### Cookbook:

1. clone the repository:

```shell
git clone https://github.com/pherde/RailsExchange.git
```
```shell
cd RailsExchange
```

2. build:
```shell
docker-compose build
```

3. create database:
```ruby
docker-compose run --rm app bundle exec rails db:create db:migrate
```

4. set api token:

- get api token in currencydatafeed.com (there is a free account)
- log in the machine:
```shell
docker-compose run --rm app bash
```
- open editor:
```shell
EDITOR=vim bundle exec rails credentials:edit
```
- insert the lines below and save:
```ruby
test:
  secret_key_base: c6658efe5424dd97a9e651608915f7fd6205e4e8c8411c93657c9896279cac6625cf23cd3989c30cfebeab595f97d4deaf70e25d888bd7b71af41702e9a36ae6
  currency_api_key: your_api_key
  currency_api_url: https://currencydatafeed.com/api/data.php
 
 
development:
  secret_key_base: c6658efe5424dd97a9e651608915f7fd6205e4e8c8411c93657c9896279cac6625cf23cd3989c30cfebeab595f97d4deaf70e25d888bd7b71af41702e9a36ae6
  currency_api_key: your_api_key
  currency_api_url: https://currencydatafeed.com/api/data.php
 
 
production:
  secret_key_base: c6658efe5424dd97a9e651608915f7fd6205e4e8c8411c93657c9896279cac6625cf23cd3989c30cfebeab595f97d4deaf70e25d888bd7b71af41702e9a36ae6
  currency_api_key: your_api_key
  currency_api_url: https://currencydatafeed.com/api/data.php
```
- exit from machine:

```shell
exit
```

5. run app:

```shell
docker-compose up
```
To access: `localhost:3000`