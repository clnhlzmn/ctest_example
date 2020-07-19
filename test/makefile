SRCS = ../project_src.c test_main.c

SRC_FILES = $(notdir $(SRCS))

OBJ_FILES = $(subst .c,.o,$(SRC_FILES))

BUILDDIR = build

OBJS = $(addprefix $(BUILDDIR)/,$(OBJ_FILES))

CFLAGS = -g -std=c99 -MD -MP -I.. -c

.PHONY: test
test: $(OBJS)
	gcc $(OBJS) $(LDFLAGS) -o $(BUILDDIR)/test
	./$(BUILDDIR)/test

$(OBJS): %.o: $(filter %$(notdir $(subst .o,.c,$@)),$(SRCS)) | $(BUILDDIR)
	gcc $(filter %$(notdir $(subst .o,.c,$@)),$(SRCS)) $(CFLAGS) -o $@

include $(wildcard $(BUILDDIR)/*.d)

$(BUILDDIR): 
	mkdir $(BUILDDIR)

.PHONY: clean
clean:
	rm -rf $(BUILDDIR)

.PHONY: show
show: 
	@echo $(OBJS)