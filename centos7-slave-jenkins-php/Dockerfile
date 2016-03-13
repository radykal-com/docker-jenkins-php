# The MIT License
#
#  Permission is hereby granted, free of charge, to any person obtaining a copy
#  of this software and associated documentation files (the "Software"), to deal
#  in the Software without restriction, including without limitation the rights
#  to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
#  copies of the Software, and to permit persons to whom the Software is
#  furnished to do so, subject to the following conditions:
#
#  The above copyright notice and this permission notice shall be included in
#  all copies or substantial portions of the Software.
#
#  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#  IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#  FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
#  AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#  LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
#  OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
#  THE SOFTWARE.

# THIS IMAGE ONLY CONTAINS ALL THE TOOLS USED IN JENKINS-PHP TEMPLATE
# DOES NOT CONTAIN ANY PHP VERSION INSTALLED.
# EXTEND THIS IMAGE WITH YOUR REQUIRED PHP VERSION TO RUN THE TESTS

FROM radykal/centos7-slave-jenkins:latest
MAINTAINER Marc Ruiz -radykal- <radykal@radykal.com>

#INSTALL PHP-JENKINS TOOLS
RUN wget https://getcomposer.org/composer.phar \
	&& chmod +x composer.phar \
	&& mv composer.phar /usr/local/bin/composer

RUN wget https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar \
	&& chmod +x phpcs.phar \
	&& mv phpcs.phar /usr/local/bin/phpcs

RUN wget https://phar.phpunit.de/phploc.phar \
	&& chmod +x phploc.phar \
	&& mv phploc.phar /usr/local/bin/phploc

RUN wget http://static.pdepend.org/php/latest/pdepend.phar \
	&& chmod +x pdepend.phar \
	&& mv pdepend.phar /usr/local/bin/pdepend

RUN wget http://static.phpmd.org/php/latest/phpmd.phar \
	&& chmod +x phpmd.phar \
	&& mv phpmd.phar /usr/local/bin/phpmd

RUN wget https://phar.phpunit.de/phpcpd.phar \
	&& chmod +x phpcpd.phar \
	&& mv phpcpd.phar /usr/local/bin/phpcpd

RUN wget http://phpdox.de/releases/phpdox.phar \
	&& chmod +x phpdox.phar \
	&& mv phpdox.phar /usr/local/bin/phpdox

RUN wget https://phar.phpunit.de/phpunit.phar \
	&& chmod +x phpunit.phar \
	&& mv phpunit.phar /usr/local/bin/phpunit
