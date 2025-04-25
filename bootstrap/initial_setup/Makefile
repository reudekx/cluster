.PHONY: all check_vars initial_setup

USAGE := Usage: make USER=<target_user> HOST=<target_host_ip>

all: initial_setup

check_vars:
	$(if $(filter command line, $(origin USER)), , $(error $(USAGE)))
	$(if $(filter command line, $(origin HOST)), , $(error $(USAGE)))

initial_setup: check_vars
	@ssh-copy-id $(USER)@$(HOST)
	@cd ansible && ansible-playbook -i $(USER)@$(HOST), site.yml -K
