
.PHONY: environment remove-env install uninstall test # .PHONY is something we can add when our target dependencies are not files.

MODULE=mcsim
ENVIRONMENT=chem274A_lab1

//creates the evnironment but first checks to see if the environment is already present and removes it. 
environment: remove-env
	conda create -n $(ENVIRONMENT) "python=3.9" --yes
	conda install -c conda-forge notebook nbconvert numpy matplotlib pytest-cov pandas --name $(ENVIRONMENT) --yes

//The above command depends on this target and utilizes this command to remove the environment.
remove-env:
	conda remove --name $(ENVIRONMENT) --all --yes

//installs the package but first checks to make sure if the package is already present and removes it. Thi is the uneditable version.  
install: uninstall ## install the package to the active Python's site-packages
	pip install .

/installs the editable version of the package and it also checks to make sure there are no other versions of the package in the system. 
dev-install: uninstall
	pip install -e .

//The above two commands depend on this target to execute this to ensure that all the packages are unintalled. 
uninstall: ## uninstall the package
	pip uninstall --yes $(MODULE)

//will perform the provided tests
test: 
	pytest -v
