# Copyright 2021 the V8 project authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.

workspace(name = "v8")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "bazel_skylib",
    sha256 = "bc283cdfcd526a52c3201279cda4bc298652efa898b10b4db0837dc51652756f",
    urls = [
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.7.1/bazel-skylib-1.7.1.tar.gz",
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.7.1/bazel-skylib-1.7.1.tar.gz",
    ],
)

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

bazel_skylib_workspace()

http_archive(
    name = "rules_python",
    sha256 = "a30abdfc7126d497a7698c29c46ea9901c6392d6ed315171a6df5ce433aa4502",
    strip_prefix = "rules_python-0.6.0",
    url = "https://github.com/bazelbuild/rules_python/archive/0.6.0.tar.gz",
)

load("@rules_python//python:pip.bzl", "pip_install")

pip_install(
    name = "v8_python_deps",
    extra_pip_args = ["--require-hashes"],
    requirements = "//:bazel/requirements.txt",
)

new_local_repository(
    name = "com_googlesource_chromium_zlib",
    build_file = "bazel/BUILD.zlib",
    path = "third_party/zlib",
)

bind(
    name = "zlib",
    actual = "@com_googlesource_chromium_zlib//:zlib",
)

bind(
    name = "zlib_compression_utils",
    actual = "@com_googlesource_chromium_zlib//:zlib_compression_utils",
)

new_local_repository(
    name = "com_googlesource_chromium_icu",
    build_file = "bazel/BUILD.icu",
    path = "third_party/icu",
)

bind(
    name = "icu",
    actual = "@com_googlesource_chromium_icu//:icu",
)

new_local_repository(
    name = "com_googlesource_chromium_base_trace_event_common",
    build_file = "bazel/BUILD.trace_event_common",
    path = "base/trace_event/common",
)

bind(
    name = "base_trace_event_common",
    actual = "@com_googlesource_chromium_base_trace_event_common//:trace_event_common",
)
