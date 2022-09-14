workspace(
    name = "repro_wksp",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_rust",
    sha256 = "0cc7e6b39e492710b819e00d48f2210ae626b717a3ab96e048c43ab57e61d204",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_rust/releases/download/0.10.0/rules_rust-v0.10.0.tar.gz",
        "https://github.com/bazelbuild/rules_rust/releases/download/0.10.0/rules_rust-v0.10.0.tar.gz",
    ],
)

load("@rules_rust//rust:repositories.bzl", "rust_repositories")

rust_repositories(
    edition = "2021",
    include_rustc_srcs = False,
)

load("@rules_rust//crate_universe:defs.bzl", "crates_repository")

crates_repository(
    name = "cratesweb",
    cargo_lockfile = "//rust:Cargo.lock",
    #lockfile = "//rust:Bazel.lock",
    manifests = [
        "//rust:Cargo.toml",
        "//rust/s3lib:Cargo.toml",
        "//rust/warplib:Cargo.toml",
    ],
)

load("@cratesweb//:defs.bzl", "crate_repositories")

crate_repositories()
