.PHONY: all check_vars bootstrap

USAGE := Usage: make USER=<target_user> HOST=<target_host_ip>

all: bootstrap

check_vars:
	$(if $(filter command line, $(origin USER)), , $(error $(USAGE)))
	$(if $(filter command line, $(origin HOST)), , $(error $(USAGE)))

bootstrap: check_vars
	@ssh-copy-id $(USER)@$(HOST)
	@cd ansible && ansible-playbook -i $(USER)@$(HOST), bootstrap.yml -K
