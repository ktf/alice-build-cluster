load("@rules_foreign_cc//tools/build_defs:cmake.bzl", "cmake_external")
load("@rules_foreign_cc//tools/build_defs:configure.bzl", "configure_make")

configure_make(
    name = "m4",
    configure_options = [
        "--disable-dependecy-tracking",
    ],
    configure_env_vars = {
      "AR": "",
    },
    lib_source = "@m4_sources//:all",
)

configure_make(
    name = "sqlite",
    configure_options = [
        "--disable-dependecy-tracking",
        "--disable-shared"
    ],
    configure_env_vars = {
      "AR": "",
    },
    lib_source = "@sqlite_sources//:all",
    static_libraries = [
        "libsqlite3.a",
    ],
)

configure_make(
    name = "openssl",
    configure_command = "config",
    configure_options = [
        "no-shared",
    ],
    lib_source = "@openssl_sources//:all",
    configure_env_vars = {
      "AR": "",
    },
    static_libraries = [
        "libcrypto.a",
        "libssl.a",
    ],
)

configure_make(
    name = "apr",
    configure_options = [
        "--enable-shared=no",
    ],
    configure_env_vars = {
      "AR": "",
    },
    lib_source = "@apr_sources//:all",
    static_libraries = ["libapr-1.a"],
)

configure_make(
    name = "apr_util",
    lib_source = "@apr_util_sources//:all",
    deps = [":apr"],
    configure_options = [
        "--with-apr=$$EXT_BUILD_DEPS$$/apr",
        ],
    configure_env_vars = {
      "AR": "",
      "CPP": "cpp",
      "LIBTOOL": "libtool",
    },
    static_libraries = ["libaprutil-1.a"],
)

configure_make(
    name = "svn",
    lib_source = "@svn_sources//:all",
    deps = [":apr", ":apr_util"],
    configure_options = [
        "--with-apr=$$EXT_BUILD_DEPS$$/apr",
        "--with-apr-util=$$EXT_BUILD_DEPS$$/apr_util",
        "--with-lz4=internal",
        "--with-sqlite=$$EXT_BUILD_DEPS$$/sqlite",
        "--with-utf8proc=internal",
        "CFLAGS='-Dredacted=\"redacted\"'"
        ],
    configure_env_vars = {
      "AR": "",
      "CPP": "cpp",
    },
    static_libraries = ["libsvn_subr-1.a", "libsvn_delta-1.a"],
)

configure_make(
    name = "python",
    lib_source = "@python_sources//:all",
    deps = [],
    configure_options = [
      "--disable-shared",
      "CFLAGS='-Dredacted=\"redacted\"'"
        ],
    configure_env_vars = {
      "AR": "",
      "CPP": "cpp",
    },
    out_lib_dir = "lib",
    static_libraries = ["libpython2.7.a"],
)

configure_make(
   name = "mesos",
   # Values to be passed as -Dkey=value on the CMake command line;
   # here are serving to provide some CMake script configuration options
   lib_source = "@mesos_sources//:all",
   deps = [":apr", ":svn", ":python"],
   configure_options = [
       "--with-apr=$$EXT_BUILD_DEPS$$/apr",
       "--with-apr-util=$$EXT_BUILD_DEPS$$/apr_util",
       "--with-svn=$$EXT_BUILD_DEPS$$/svn",
       "--with-python=$$EXT_BUILD_DEPS$$/python",
       "--disable-java",
       "--disable-python"
       ],
   configure_env_vars = {
     "AR": "",
     "CC": "clang",
     "CXX": "clang++",
     "LDFLAGS": "-lstdc++"
   },

   # We are selecting the resulting static library to be passed in C/C++ provider
   # as the result of the build;
   # However, the cmake_external dependants could use other artefacts provided by the build,
   # according to their CMake script
   static_libraries = ["libmesos.a"],
)
