NAME = ocaml-top

SRC = cfg.ml tools.mli tools.ml top.mli top.ml gui.mli gui.ml ocamlBuffer.mli ocamlBuffer.ml topUi.mli topUi.ml main.ml
# temporarily disabled: completion.mli completion.ml
OCAMLFIND_OPTS = -package unix,lablgtk2,lablgtk2.sourceview2,str,ocp-indent-lib -linkpkg -thread -g
# temporarily removed: ocp-index-lib

UNAME := $(shell uname)
ifeq (WIN,$(findstring WIN,$(UNAME)))
  EXEEXT := .exe
  SRC += sigint_win.c
else
  EXEEXT :=
  SRC += sigint_unix.c
endif

$(NAME)-byte$(EXEEXT): $(SRC)
	ocamlfind ocamlc -custom $(OCAMLFIND_OPTS) $(SRC) -o $@

$(NAME)$(EXEEXT): $(SRC)
	ocamlfind ocamlopt $(OCAMLFIND_OPTS) $(SRC) -o $@

.PHONY: clean
clean:
	rm -f *.o *.cm* $(NAME)-byte$(EXEEXT) $(NAME)$(EXEEXT)
