load("ext://docker_build_sub", "docker_build_sub")

docker_compose(["./docker-compose.yml"])
docker_build_sub(
    "rwoll/core:repro",
    "./services/core",
    child_context="./deps",
    extra_cmds=[
        "COPY ./example.txt .",
    ],
)

docker_build_sub(
    "rwoll/extra:repro",
    "./services/extra",
    child_context="./deps",
    extra_cmds=[
        "COPY ./example.txt .",
    ],
)


dc_resource("extra", auto_init=False)
