package(default_visibility = ["//app:__subpackages__"])

reason_module(
    name = "src",
    srcs = glob(["*.re"]),
)

bs_module(
    name = "Components",
    srcs = [":src"],
    config = "//:bs_config",
    deps = [],
)
