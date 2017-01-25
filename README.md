# hacku-devops-gunicorn-docker
docker image for booting up a gunicorn server

Project to boot up and serve basic docker image with testing.

## Running the Application

docker-compose up

## Unit Tests

Run some tests

docker-compose run web python manage.py test
Create a file called scent.py with the following contents:

from subprocess import call
from sniffer.api import runnable

    @runnable
    def execute_tests(*args):
        fn = [ 'python', 'manage.py', 'test' ]
        fn += args[1:]
        return call(fn) == 0
    From the command line:

docker-compose run web sniffer
This will automatically run the tests each time you make changes to the code

## Unit Test Coverage Reporting

Generate code coverage report to stdout From the command line:
docker-compose run web coverage run --source='.'  manage.py test
Generate code coverage report to HTML
docker-compose run web coverage html --directory=reports
You will then find your coverage report in reports/index.html
