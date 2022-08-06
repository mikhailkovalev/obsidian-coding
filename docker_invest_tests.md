```bash
# построение образа
docker build --build-arg=VERSION=`/bin/bash ./deploy/version.sh` -f Dockerfile.tests -t "invest-tests:local"

# запуск тестов с переопределением entrypoint и пробросом volume
docker-compose
    -f ./deploy/tests.docker-compose.yml
	run
	--entrypoint "pytest tests/test_accept_borrow_finish.py::test_basic"
	-v "/absolute/local/path:/container/path"
	tests
```