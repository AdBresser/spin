AM_CPPFLAGS = -I$(top_srcdir)/include -Wall -Werror
AM_CFLAGS = ${regular_CFLAGS} -g

CLEANFILES = *.gcda *.gcno *.gcov

bin_PROGRAMS = tree_test node_cache_test arp_test node_names_test util_test dns_cache_test netlink_commands_test

tree_test_SOURCES = tree_test.c ../tree.c ../util.c ../spin_log.c
tree_test_CFLAGS = -I../ -fprofile-arcs -ftest-coverage
tree_test_LDFLAGS = -L../

node_cache_test_SOURCES = node_cache_test.c ../node_cache.c ../node_names.c ../util.c ../tree.c ../../kernelmod/pkt_info.c ../arp.c ../netlink_commands.c ../spin_log.c
node_cache_test_CFLAGS = -I../ -I../../kernelmod -fprofile-arcs -ftest-coverage
node_cache_test_LDFLAGS = -L../ -L../../kernelmod

dns_cache_test_SOURCES = dns_cache_test.c ../dns_cache.c ../util.c ../tree.c ../../kernelmod/pkt_info.c ../spin_log.c
dns_cache_test_CFLAGS = -I../ -I../../kernelmod -fprofile-arcs -ftest-coverage
dns_cache_test_LDFLAGS = -L../ -L../../kernelmod


arp_test_SOURCES = arp_test.c ../arp.c ../util.c ../tree.c ../spin_log.c
arp_test_CFLAGS = -I../ -fprofile-arcs -ftest-coverage
arp_test_LDFLAGS = -L../

node_names_test_SOURCES = node_names_test.c ../node_names.c ../util.c ../tree.c ../spin_log.c
node_names_test_CFLAGS = -I../ -fprofile-arcs -ftest-coverage
node_names_test_LDFLAGS = -L../

util_test_SOURCES = util_test.c ../util.c ../tree.c ../../kernelmod/pkt_info.c ../spin_log.c
util_test_CFLAGS = -I../ -I../../kernelmod -fprofile-arcs -ftest-coverage
util_test_LDFLAGS = -L../

netlink_commands_test_SOURCES = netlink_commands_test.c ../netlink_commands.c ../util.c ../tree.c ../spin_log.c
netlink_commands_test_CFLAGS = -I../ -I../../kernelmod -fprofile-arcs -ftest-coverage
netlink_commands_test_LDFLAGS = -L../ -L../../kernelmod

all-local:
	./run_tests.sh
