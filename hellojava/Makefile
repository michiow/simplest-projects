sources = $(wildcard *.java)

%.class: %.java
	javac $<

.PHONY: all
all: $(sources:%.java=%.class)

.PHONY: clean
clean:
	rm -f *.class

