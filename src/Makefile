FLAGS= -std=c11 -Wall -Werror -Wextra
COVERAGE=

all: clean s21_string.a
deafult: all
s21_string.o:
	gcc $(FLAGS) -c functions/*.c
s21_string.a: s21_string.o s21_sprintf.o
	ar cr s21_string.a *.o
clean:
	rm -rf *.a *.o *.out *.html *.css *.gcno *.gcov *.gcda s21_test
test: clean
	gcc $(FLAGS) $(COVERAGE) -o s21_test tests/*.c functions/*.c -lcheck -lm
add_coverage_flag:
	$(eval FLAGS += --coverage)
gcov_report: add_coverage_flag test
	./s21_test
	lcov -t "stest" -o s21_test.info -c -d .
	genhtml -o report s21_test.info

