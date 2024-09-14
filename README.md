# Multi-Module Project setup for Python

- python -m pip install --upgrade poetry
- Run `make docker-run`

## Other commands
~~~
clean-parent                    Remove distribution and report directories
clean                           Clean all applications
dist-clean                      Deep clean all applications
build                           Build all applications
update                          Update all applications
test                            Test all applications
cover                           Generate coverage reports for all applications
ssap                            generate required reports for ssap
package                         Package all applications
ci-prebuild                     Install specified version of Poetry
ci                              Clean, build, and package all applications
docker-build                    Will create docker image
docker-run                      Will create docker image and run docker image in random port
help                            Show make target documentation
~~~