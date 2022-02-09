# ci-containers [![Build Status](https://dev.azure.com/ret0171/PQClean%20ci-containers/_apis/build/status/CI%20containers?branchName=master)](https://dev.azure.com/ret0171/PQClean%20ci-containers/_build/latest?definitionId=3&branchName=master)

Containers with CI configurations for the [PQClean main project](https://github.com/PQClean/PQClean).

This repository contains Dockerfiles that assist CI in the PQClean repository.
They are built using travis ci, which should update them at least once weekly.

The current containers are derivations from the `$arch/debian` containers and you should run the following command before trying to launch one of them:

    docker run --rm --privileged multiarch/qemu-user-static --reset -p yes
