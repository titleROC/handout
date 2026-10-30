# 编译讲义（需 XeLaTeX + latexmk）
#   make          同时生成教师版与学生版
#   make teacher  只生成教师版
#   make student  只生成学生版
#   make clean    清理中间文件

LATEXMK = latexmk -xelatex -interaction=nonstopmode -halt-on-error -file-line-error -outdir=build
SOURCES = main.tex student.tex preamble.tex $(wildcard sections/*.tex)

TEACHER_PDF = 涡流及其应用-教师版.pdf
STUDENT_PDF = 涡流及其应用-学生版.pdf

.PHONY: all teacher student clean

all: teacher student

teacher: $(TEACHER_PDF)
student: $(STUDENT_PDF)

$(TEACHER_PDF): $(SOURCES)
	$(LATEXMK) main.tex
	cp build/main.pdf "$@"

$(STUDENT_PDF): $(SOURCES)
	$(LATEXMK) student.tex
	cp build/student.pdf "$@"

clean:
	latexmk -C -outdir=build main.tex student.tex
	rm -rf build
