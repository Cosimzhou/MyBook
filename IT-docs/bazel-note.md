Bazel note
==========

# CLI

```bash
bazel build //root/package:target
bazel build --compilation_mode=dbg -s //root/path:target    # = -c dbg
bazel build --compilation_mode=opt -s //root/path:target    # = -c opt

bazel build --copt //root/package:target

bazel build //root/path:target
bazel build --config <config_setting> //root/path:target

bazel test //root/package:target_name
bazel test //package/...

bazel run //root/package:target_name

bazel clean

bazel version

bazel info
bazel info output_base
bazel info 2>&-|grep output_base:

bazel query --notool_deps --noimplicit_deps "deps(//main:hello-world)" --output graph | dot -Tpng > hello-world.png
bazel query "deps\(//deepmap_api_impl/feature_service:feature_service_impl\)"|grep "^@"|awk -F/ '{print $1}'|sort -u
bazel query 'allpaths\(deepmap_api_impl/feature_service:feature_service_impl, @precompiled_ceres_suitesparse//:ceres_lib\)'
bazel query 'allpaths\(deepmap_api_impl/feature_service:feature_service_impl, @aws_sdk_lib//:aws_lib\)'
```



```
package_path=public/deepmap_api/protos
mkdir -p {cpp,python}/${package_path}
bazel build --compilation_mode=dbg -s //deepmap_api_impl/map_engine:map_engine_grpc_server
cp bazel-out/k8-dbg/bin/${package_path}/*.pb.{cc,h} \
bazel-out/k8-dbg/bin/${package_path}/map_engine_service_grpc_lib_pb/${package_path}/* cpp/${package_path}

bazel build --compilation_mode=dbg -s //${package_path}/...
cp bazel-bin/${package_path}/*_python_proto/${package_path}/*.py python/${package_path}

bazel build --compilation_mode=dbg -s //root/path:target
bazel info
cp bazel-out/k8-dbg/bin/${package_path}/*.pb.{cc,h} \
bazel-out/k8-dbg/bin/${package_path}/map_engine_service_grpc_lib_pb/${package_path}/* \
cpp/${package_path}

bazel build --compilation_mode=dbg -s //${package_path}/...
cp bazel-bin/${package_path}/*_python_proto/${package_path}/*.py python/${package_path}
```

dazel runs bazel in a certain docker container. 

bazelisk will download and install a specified version bazel according to the .bazelversion file under the root directory of the workspace, and run the specified bazel automatically.

# Language starlark

.bzl  written in starlark, which is a restricted Python
BUILD  written in skylark, which is more restricted than starklark and no method defining

builtin in bazel .bzl
package(default_visibility=["//visibility:public"])
load("package", funcs, ...)
bind(name="package", actual="@repo//:package")
native.cc_library
native.py_library
native.java_library
native.genrule

external library: imported from WORKSPACE file


bazelisk    # A user-friendly launcher for Bazel.

