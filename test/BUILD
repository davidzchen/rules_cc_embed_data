# Copyright 2019 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("//embed_data:build_defs.bzl", "cc_embed_data")

cc_embed_data(
    name = "testembed1",
    # do not sort
    srcs = [
        "file1.txt",
        "data/file2.txt",
    ],
    cc_file_output = "testembed1.cc",
    cpp_namespace = "foobar",
    flatten = True,
    h_file_output = "testembed1.h",
)

cc_embed_data(
    name = "testembed2",
    srcs = [
        "data/file3.txt",
    ],
    cc_file_output = "testembed2.cc",
    cpp_namespace = "foobar",
    flatten = True,
    h_file_output = "testembed2.h",
)

cc_test(
    name = "cc_embed_data_test",
    srcs = ["cc_embed_data_test.cc"],
    deps = [
        ":testembed1",
        ":testembed2",
        "@googletest//:gtest_main",
    ],
)
