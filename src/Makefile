CC = gcc -std=c11
CFLAGS = -g -Wall -Wextra -Werror
CHECKFLAGS = -lcheck -lsubunit -lm -lrt -lpthread
GCOVFLAGS = -fprofile-arcs -ftest-coverage
MODULES_O = calc.o comparisions.o copy.o helping.o search.o spec.o sprintf.o

MODULE_1_C = calc.c
MODULE_2_C = comparisions.c
MODULE_3_C = copy.c
MODULE_4_C = helping.c
MODULE_5_C = search.c
MODULE_6_C = spec.c
MODULE_7_C = sprintf.c

MODULE_1_O = calc.o
MODULE_2_O = comparisions.o
MODULE_3_O = copy.o
MODULE_4_O = helping.o
MODULE_5_O = search.o
MODULE_6_O = spec.o
MODULE_7_O = sprintf.o

MODULES_TEST = tests/test_insert.c tests/test_memchr.c tests/test_memcmp.c tests/test_memcpy.c tests/test_memmove.c tests/test_memset.c tests/test_sprintf_c.c tests/test_sprintf_d.c tests/test_sprintf_e.c tests/test_sprintf_f.c tests/test_sprintf_g.c tests/test_sprintf_hex1.c tests/test_sprintf_hex2.c tests/test_sprintf_i.c tests/test_sprintf_n.c tests/test_sprintf_octal.c tests/test_sprintf_percent.c tests/test_sprintf_pointer.c tests/test_sprintf_string.c tests/test_sprintf_unsigned.c tests/test_srtcpy.c tests/test_sscanf_c.c tests/test_sscanf_d.c tests/test_sscanf_empty.c tests/test_sscanf_i.c tests/test_sscanf_n.c tests/test_sscanf_o.c tests/test_sscanf_p.c tests/test_sscanf_real.c tests/test_sscanf_x.c tests/test_strcat.c tests/test_strchr.c tests/test_strcmp.c tests/test_strcspn.c tests/test_strerror.c tests/test_strlen.c tests/test_strncat.c tests/test_strncmp.c tests/test_strncpy.c tests/test_strpbrk.c tests/test_strrchr.c tests/test_strspn.c tests/test_strstr.c tests/test_strtok.c tests/test_to_lower.c tests/test_to_upper.c tests/test_trim.c tests/test_me.c

.PHONY: all clean

all: string.a test
 string.a: $(MODULES_O)
	ar rcs $@ $^

$(MODULE_1_O): $(MODULE_1_C)
	$(CC) -c $(CFLAGS) -o $@ $^

$(MODULE_2_O): $(MODULE_2_C)
	$(CC) -c $(CFLAGS) -o $@ $^

$(MODULE_3_O): $(MODULE_3_C)
	$(CC) -c $(CFLAGS) -o $@ $^

$(MODULE_4_O): $(MODULE_4_C)
	$(CC) -c $(CFLAGS) -o $@ $^

$(MODULE_5_O): $(MODULE_5_C)
	$(CC) -c $(CFLAGS) -o $@ $^

$(MODULE_6_O): $(MODULE_6_C)
	$(CC) -c $(CFLAGS) -o $@ $^

$(MODULE_7_O): $(MODULE_7_C)
	$(CC) -c $(CFLAGS) -o $@ $^

clean:
	rm -f *.out *.o *.a *.so *.gcno *.gcda

run:
	. string.out

.SILENT: string_gcov.out gcov_report

gcov_report: clean string_gcov.out
	. string_gcov.out
	gcovr -r . --html -o string.html
 string_gcov.out: $(MODULES_TEST) string.a
	$(CC) $(CFLAGS) $(GCOVFLAGS) -o $@ $^ $(CHECKFLAGS)

test: string_test.out
 string_test.out: $(MODULES_TEST) string.a
	$(CC) $(CFLAGS) -o $@ $^ $(CHECKFLAGS)

test_run:
	. string_test.out
