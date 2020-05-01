workspace(name = "mesos")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

all_content = """filegroup(name = "all", srcs = glob(["**"]), visibility = ["//visibility:public"])"""

http_archive(
   name = "rules_foreign_cc",
   sha256 = "817c93454dce5feb0fc231c39300c016c74bb6acec223f35d052521b585d4e78",
   strip_prefix = "rules_foreign_cc-master",
   url = "https://github.com/ktf/rules_foreign_cc/archive/master.zip",
)

load("@rules_foreign_cc//:workspace_definitions.bzl", "rules_foreign_cc_dependencies")

rules_foreign_cc_dependencies([])


http_archive(
  name = "python_sources",
  sha256 = "304c9b202ea6fbd0a4a8e0ad3733715fbd4749f2204a9173a58ec53c32ea73e8",
  build_file_content = all_content,
  strip_prefix = "Python-2.7.14",
  urls = ["https://www.python.org/ftp/python/2.7.14/Python-2.7.14.tgz"]
)

http_archive(
   name = "m4_sources",
   build_file_content = all_content,
   strip_prefix = "m4-1.4.18/",
   urls = ["https://ftp.gnu.org/gnu/m4/m4-1.4.18.tar.gz"]
)

http_archive(
   name = "openssl_sources",
   build_file_content = all_content,
   strip_prefix = "openssl-1.1.1g",
   urls = ["https://www.openssl.org/source/openssl-1.1.1g.tar.gz"]
)

http_archive(
   name = "apr_sources",
   build_file_content = all_content,
   strip_prefix = "apr-1.7.0/",
   urls = ["https://pub.tutosfaciles48.fr/mirrors/apache/apr/apr-1.7.0.tar.gz"]
)

http_archive(
   name = "apr_util_sources",
   build_file_content = all_content,
   strip_prefix = "apr-util-1.6.1/",
   urls = ["https://apache.mirror.schettada.io//apr/apr-util-1.6.1.tar.gz"]
)

http_archive(
   name = "svn_sources",
   sha256 = "daad440c03b8a86fcca804ea82217bb1902cfcae1b7d28c624143c58dcb96931",
   build_file_content = all_content,
   strip_prefix = "subversion-1.13.0/",
   urls = ["https://mirror.ibcp.fr/pub/apache/subversion/subversion-1.13.0.tar.gz"]
)

http_archive(
   name = "mesos_sources",
   patch_cmds = ["./bootstrap"],
   build_file_content = all_content,
   strip_prefix = "mesos-1.1.2/",
   urls = ["https://github.com/apache/mesos/archive/1.1.2.tar.gz"],
)
