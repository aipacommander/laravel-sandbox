export PWD=`pwd`
export COMPOSER_RUN=docker run --rm -u "$(id -u):$(id -g)" -v $(PWD):/var/www/html -w /var/www/html laravelsail/php81-composer:latest composer
export INSTALL=$(COMPOSER_RUN) install --ignore-platform-reqs
export REQUIRE=$(COMPOSER_RUN) require

install:
	$(INSTALL)
install_args:
	$(REQUIRE) $(package)
test:
	./vendor/bin/sail artisan migrate:refresh --seed
	./vendor/bin/sail artisan test --parallel
phpcs:
	./vendor/bin/sail composer phpcs
phpcbf:
	./vendor/bin/sail composer phpcbf
all:
	@make test
	@make phpcbf
	@make phpcs