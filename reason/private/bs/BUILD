package(default_visibility = ["//:__subpackages__"])

load("//reason/private:utils.bzl", "unpack_filegroup")

"""
Build the BuckleScript compiler using the patched Ocaml compiler.

The output of this rule is a tar file with all of the compiled BuckleScript
platform.
"""

genrule(
    name = "make_world",
    srcs = ["@bs//:srcs"],
    outs = ["bs_platform.tar"],
    cmd = """\
      #!/bin/bash

      # compute this package's root directory
      pkg_root=$$(dirname $(location :bs_platform.tar))

      # copy over all bucklescript sources
      cp -fR external/bs/* $$pkg_root;

      # build ocaml compiler first
      pushd $$pkg_root/vendor/ocaml;

        ./configure --prefix $$(pwd);
        make world.opt -j4;
        make install;

      popd;

      # build bucklescript compiler second!
      pushd $$pkg_root;

        PATH=$$(pwd)/vendor/ocaml/bin:$$PATH make;
        make install;

      popd;

      # output the compiled workspace
      tar --transform "s=$$pkg_root/==g" \
          --create $$pkg_root \
          --dereference \
          > $(location :bs_platform.tar);
  """,
)

genrule(
    name = "bundle_targets",
    srcs = [":bs_platform.tar"],
    outs = [
        "bucklescript.bins.tar",
        "stdlib.ml.tar",
        "stdlib.js.tar",
    ],
    cmd = """\

      # compute this package's root directory
      pkg_root=$$(dirname $(location :bs_platform.tar))

      # unpack bs-platform
      tar --extract \
          --file $$(pwd)/$(location :bs_platform.tar) \
          --directory $(@D);

      # pack bucklescript binaries
      tar --transform "s=$$pkg_root/lib/==g" \
          --create $$pkg_root/lib/*.exe \
          > $(location :bucklescript.bins.tar);

      # pack ml stdlib preserving paths
      tar --transform "s=$$pkg_root/==g" \
          --create $$pkg_root/lib/ocaml/* \
          --dereference \
          > $(location stdlib.ml.tar);

      # pack js stdlib preserving paths
      tar --transform "s=$$pkg_root/==g" \
          --create $$pkg_root/lib/js/* \
          --dereference \
          > $(location stdlib.js.tar);

    """,
)

genrule(
    name = "unpack_bsb_binaries",
    srcs = [":bucklescript.bins.tar"],
    outs = [
        "bsb.exe",
        "bsb_helper.exe",
        "bsc.exe",
        "bsppx.exe",
        "refmt.exe",
    ],
    cmd = """\
      #!/bin/bash

      tar --extract \
          --file $(location :bucklescript.bins.tar) \
          --directory $(@D);

      """,
)

ml_files = [
    "lib/ocaml/arg.cmi",
    "lib/ocaml/arg.cmj",
    "lib/ocaml/arg.cmt",
    "lib/ocaml/arg.cmti",
    "lib/ocaml/arg.ml",
    "lib/ocaml/arg.mli",
    "lib/ocaml/array.cmi",
    "lib/ocaml/array.cmj",
    "lib/ocaml/array.cmt",
    "lib/ocaml/array.cmti",
    "lib/ocaml/array.ml",
    "lib/ocaml/array.mli",
    "lib/ocaml/arrayLabels.cmi",
    "lib/ocaml/arrayLabels.cmj",
    "lib/ocaml/arrayLabels.cmt",
    "lib/ocaml/arrayLabels.cmti",
    "lib/ocaml/arrayLabels.ml",
    "lib/ocaml/arrayLabels.mli",
    "lib/ocaml/belt.cmi",
    "lib/ocaml/belt.cmj",
    "lib/ocaml/belt.cmt",
    "lib/ocaml/belt.ml",
    "lib/ocaml/belt_Array.cmi",
    "lib/ocaml/belt_Array.cmj",
    "lib/ocaml/belt_Array.cmt",
    "lib/ocaml/belt_Array.cmti",
    "lib/ocaml/belt_Array.ml",
    "lib/ocaml/belt_Array.mli",
    "lib/ocaml/belt_Debug.cmi",
    "lib/ocaml/belt_Debug.cmj",
    "lib/ocaml/belt_Debug.cmt",
    "lib/ocaml/belt_Debug.ml",
    "lib/ocaml/belt_HashMap.cmi",
    "lib/ocaml/belt_HashMap.cmj",
    "lib/ocaml/belt_HashMap.cmt",
    "lib/ocaml/belt_HashMap.cmti",
    "lib/ocaml/belt_HashMap.ml",
    "lib/ocaml/belt_HashMap.mli",
    "lib/ocaml/belt_HashMapInt.cmi",
    "lib/ocaml/belt_HashMapInt.cmj",
    "lib/ocaml/belt_HashMapInt.cmt",
    "lib/ocaml/belt_HashMapInt.cmti",
    "lib/ocaml/belt_HashMapInt.ml",
    "lib/ocaml/belt_HashMapInt.mli",
    "lib/ocaml/belt_HashMapString.cmi",
    "lib/ocaml/belt_HashMapString.cmj",
    "lib/ocaml/belt_HashMapString.cmt",
    "lib/ocaml/belt_HashMapString.cmti",
    "lib/ocaml/belt_HashMapString.ml",
    "lib/ocaml/belt_HashMapString.mli",
    "lib/ocaml/belt_HashSet.cmi",
    "lib/ocaml/belt_HashSet.cmj",
    "lib/ocaml/belt_HashSet.cmt",
    "lib/ocaml/belt_HashSet.cmti",
    "lib/ocaml/belt_HashSet.ml",
    "lib/ocaml/belt_HashSet.mli",
    "lib/ocaml/belt_HashSetInt.cmi",
    "lib/ocaml/belt_HashSetInt.cmj",
    "lib/ocaml/belt_HashSetInt.cmt",
    "lib/ocaml/belt_HashSetInt.cmti",
    "lib/ocaml/belt_HashSetInt.ml",
    "lib/ocaml/belt_HashSetInt.mli",
    "lib/ocaml/belt_HashSetString.cmi",
    "lib/ocaml/belt_HashSetString.cmj",
    "lib/ocaml/belt_HashSetString.cmt",
    "lib/ocaml/belt_HashSetString.cmti",
    "lib/ocaml/belt_HashSetString.ml",
    "lib/ocaml/belt_HashSetString.mli",
    "lib/ocaml/belt_Id.cmi",
    "lib/ocaml/belt_Id.cmj",
    "lib/ocaml/belt_Id.cmt",
    "lib/ocaml/belt_Id.cmti",
    "lib/ocaml/belt_Id.ml",
    "lib/ocaml/belt_Id.mli",
    "lib/ocaml/belt_List.cmi",
    "lib/ocaml/belt_List.cmj",
    "lib/ocaml/belt_List.cmt",
    "lib/ocaml/belt_List.cmti",
    "lib/ocaml/belt_List.ml",
    "lib/ocaml/belt_List.mli",
    "lib/ocaml/belt_Map.cmi",
    "lib/ocaml/belt_Map.cmj",
    "lib/ocaml/belt_Map.cmt",
    "lib/ocaml/belt_Map.cmti",
    "lib/ocaml/belt_Map.ml",
    "lib/ocaml/belt_Map.mli",
    "lib/ocaml/belt_MapDict.cmi",
    "lib/ocaml/belt_MapDict.cmj",
    "lib/ocaml/belt_MapDict.cmt",
    "lib/ocaml/belt_MapDict.cmti",
    "lib/ocaml/belt_MapDict.ml",
    "lib/ocaml/belt_MapDict.mli",
    "lib/ocaml/belt_MapInt.cmi",
    "lib/ocaml/belt_MapInt.cmj",
    "lib/ocaml/belt_MapInt.cmt",
    "lib/ocaml/belt_MapInt.cmti",
    "lib/ocaml/belt_MapInt.ml",
    "lib/ocaml/belt_MapInt.mli",
    "lib/ocaml/belt_MapString.cmi",
    "lib/ocaml/belt_MapString.cmj",
    "lib/ocaml/belt_MapString.cmt",
    "lib/ocaml/belt_MapString.cmti",
    "lib/ocaml/belt_MapString.ml",
    "lib/ocaml/belt_MapString.mli",
    "lib/ocaml/belt_MutableMap.cmi",
    "lib/ocaml/belt_MutableMap.cmj",
    "lib/ocaml/belt_MutableMap.cmt",
    "lib/ocaml/belt_MutableMap.cmti",
    "lib/ocaml/belt_MutableMap.ml",
    "lib/ocaml/belt_MutableMap.mli",
    "lib/ocaml/belt_MutableMapInt.cmi",
    "lib/ocaml/belt_MutableMapInt.cmj",
    "lib/ocaml/belt_MutableMapInt.cmt",
    "lib/ocaml/belt_MutableMapInt.cmti",
    "lib/ocaml/belt_MutableMapInt.ml",
    "lib/ocaml/belt_MutableMapInt.mli",
    "lib/ocaml/belt_MutableMapString.cmi",
    "lib/ocaml/belt_MutableMapString.cmj",
    "lib/ocaml/belt_MutableMapString.cmt",
    "lib/ocaml/belt_MutableMapString.cmti",
    "lib/ocaml/belt_MutableMapString.ml",
    "lib/ocaml/belt_MutableMapString.mli",
    "lib/ocaml/belt_MutableQueue.cmi",
    "lib/ocaml/belt_MutableQueue.cmj",
    "lib/ocaml/belt_MutableQueue.cmt",
    "lib/ocaml/belt_MutableQueue.cmti",
    "lib/ocaml/belt_MutableQueue.ml",
    "lib/ocaml/belt_MutableQueue.mli",
    "lib/ocaml/belt_MutableSet.cmi",
    "lib/ocaml/belt_MutableSet.cmj",
    "lib/ocaml/belt_MutableSet.cmt",
    "lib/ocaml/belt_MutableSet.cmti",
    "lib/ocaml/belt_MutableSet.ml",
    "lib/ocaml/belt_MutableSet.mli",
    "lib/ocaml/belt_MutableSetInt.cmi",
    "lib/ocaml/belt_MutableSetInt.cmj",
    "lib/ocaml/belt_MutableSetInt.cmt",
    "lib/ocaml/belt_MutableSetInt.cmti",
    "lib/ocaml/belt_MutableSetInt.ml",
    "lib/ocaml/belt_MutableSetInt.mli",
    "lib/ocaml/belt_MutableSetString.cmi",
    "lib/ocaml/belt_MutableSetString.cmj",
    "lib/ocaml/belt_MutableSetString.cmt",
    "lib/ocaml/belt_MutableSetString.cmti",
    "lib/ocaml/belt_MutableSetString.ml",
    "lib/ocaml/belt_MutableSetString.mli",
    "lib/ocaml/belt_MutableStack.cmi",
    "lib/ocaml/belt_MutableStack.cmj",
    "lib/ocaml/belt_MutableStack.cmt",
    "lib/ocaml/belt_MutableStack.cmti",
    "lib/ocaml/belt_MutableStack.ml",
    "lib/ocaml/belt_MutableStack.mli",
    "lib/ocaml/belt_Option.cmi",
    "lib/ocaml/belt_Option.cmj",
    "lib/ocaml/belt_Option.cmt",
    "lib/ocaml/belt_Option.cmti",
    "lib/ocaml/belt_Option.ml",
    "lib/ocaml/belt_Option.mli",
    "lib/ocaml/belt_Range.cmi",
    "lib/ocaml/belt_Range.cmj",
    "lib/ocaml/belt_Range.cmt",
    "lib/ocaml/belt_Range.cmti",
    "lib/ocaml/belt_Range.ml",
    "lib/ocaml/belt_Range.mli",
    "lib/ocaml/belt_Result.cmi",
    "lib/ocaml/belt_Result.cmj",
    "lib/ocaml/belt_Result.cmt",
    "lib/ocaml/belt_Result.cmti",
    "lib/ocaml/belt_Result.ml",
    "lib/ocaml/belt_Result.mli",
    "lib/ocaml/belt_Set.cmi",
    "lib/ocaml/belt_Set.cmj",
    "lib/ocaml/belt_Set.cmt",
    "lib/ocaml/belt_Set.cmti",
    "lib/ocaml/belt_Set.ml",
    "lib/ocaml/belt_Set.mli",
    "lib/ocaml/belt_SetDict.cmi",
    "lib/ocaml/belt_SetDict.cmj",
    "lib/ocaml/belt_SetDict.cmt",
    "lib/ocaml/belt_SetDict.cmti",
    "lib/ocaml/belt_SetDict.ml",
    "lib/ocaml/belt_SetDict.mli",
    "lib/ocaml/belt_SetInt.cmi",
    "lib/ocaml/belt_SetInt.cmj",
    "lib/ocaml/belt_SetInt.cmt",
    "lib/ocaml/belt_SetInt.cmti",
    "lib/ocaml/belt_SetInt.ml",
    "lib/ocaml/belt_SetInt.mli",
    "lib/ocaml/belt_SetString.cmi",
    "lib/ocaml/belt_SetString.cmj",
    "lib/ocaml/belt_SetString.cmt",
    "lib/ocaml/belt_SetString.cmti",
    "lib/ocaml/belt_SetString.ml",
    "lib/ocaml/belt_SetString.mli",
    "lib/ocaml/belt_SortArray.cmi",
    "lib/ocaml/belt_SortArray.cmj",
    "lib/ocaml/belt_SortArray.cmt",
    "lib/ocaml/belt_SortArray.cmti",
    "lib/ocaml/belt_SortArray.ml",
    "lib/ocaml/belt_SortArray.mli",
    "lib/ocaml/belt_SortArrayInt.cmi",
    "lib/ocaml/belt_SortArrayInt.cmj",
    "lib/ocaml/belt_SortArrayInt.cmt",
    "lib/ocaml/belt_SortArrayInt.cmti",
    "lib/ocaml/belt_SortArrayInt.ml",
    "lib/ocaml/belt_SortArrayInt.mli",
    "lib/ocaml/belt_SortArrayString.cmi",
    "lib/ocaml/belt_SortArrayString.cmj",
    "lib/ocaml/belt_SortArrayString.cmt",
    "lib/ocaml/belt_SortArrayString.cmti",
    "lib/ocaml/belt_SortArrayString.ml",
    "lib/ocaml/belt_SortArrayString.mli",
    "lib/ocaml/belt_internalAVLset.cmi",
    "lib/ocaml/belt_internalAVLset.cmj",
    "lib/ocaml/belt_internalAVLset.cmt",
    "lib/ocaml/belt_internalAVLset.cmti",
    "lib/ocaml/belt_internalAVLset.ml",
    "lib/ocaml/belt_internalAVLset.mli",
    "lib/ocaml/belt_internalAVLtree.cmi",
    "lib/ocaml/belt_internalAVLtree.cmj",
    "lib/ocaml/belt_internalAVLtree.cmt",
    "lib/ocaml/belt_internalAVLtree.cmti",
    "lib/ocaml/belt_internalAVLtree.ml",
    "lib/ocaml/belt_internalAVLtree.mli",
    "lib/ocaml/belt_internalBuckets.cmi",
    "lib/ocaml/belt_internalBuckets.cmj",
    "lib/ocaml/belt_internalBuckets.cmt",
    "lib/ocaml/belt_internalBuckets.cmti",
    "lib/ocaml/belt_internalBuckets.ml",
    "lib/ocaml/belt_internalBuckets.mli",
    "lib/ocaml/belt_internalBucketsType.cmi",
    "lib/ocaml/belt_internalBucketsType.cmj",
    "lib/ocaml/belt_internalBucketsType.cmt",
    "lib/ocaml/belt_internalBucketsType.cmti",
    "lib/ocaml/belt_internalBucketsType.ml",
    "lib/ocaml/belt_internalBucketsType.mli",
    "lib/ocaml/belt_internalMapInt.cmi",
    "lib/ocaml/belt_internalMapInt.cmj",
    "lib/ocaml/belt_internalMapInt.cmt",
    "lib/ocaml/belt_internalMapInt.ml",
    "lib/ocaml/belt_internalMapString.cmi",
    "lib/ocaml/belt_internalMapString.cmj",
    "lib/ocaml/belt_internalMapString.cmt",
    "lib/ocaml/belt_internalMapString.ml",
    "lib/ocaml/belt_internalMutableAVLMap.ml",
    "lib/ocaml/belt_internalSetBuckets.cmi",
    "lib/ocaml/belt_internalSetBuckets.cmj",
    "lib/ocaml/belt_internalSetBuckets.cmt",
    "lib/ocaml/belt_internalSetBuckets.cmti",
    "lib/ocaml/belt_internalSetBuckets.ml",
    "lib/ocaml/belt_internalSetBuckets.mli",
    "lib/ocaml/belt_internalSetInt.cmi",
    "lib/ocaml/belt_internalSetInt.cmj",
    "lib/ocaml/belt_internalSetInt.cmt",
    "lib/ocaml/belt_internalSetInt.ml",
    "lib/ocaml/belt_internalSetString.cmi",
    "lib/ocaml/belt_internalSetString.cmj",
    "lib/ocaml/belt_internalSetString.cmt",
    "lib/ocaml/belt_internalSetString.ml",
    "lib/ocaml/bigarray.cmi",
    "lib/ocaml/bigarray.cmj",
    "lib/ocaml/bigarray.cmt",
    "lib/ocaml/bigarray.cmti",
    "lib/ocaml/bigarray.ml",
    "lib/ocaml/bigarray.mli",
    "lib/ocaml/block.cmj",
    "lib/ocaml/block.cmt",
    "lib/ocaml/block.cmti",
    "lib/ocaml/bs_obj.cmj",
    "lib/ocaml/bs_obj.cmt",
    "lib/ocaml/bs_string.cmj",
    "lib/ocaml/bs_string.cmt",
    "lib/ocaml/buffer.cmi",
    "lib/ocaml/buffer.cmj",
    "lib/ocaml/buffer.cmt",
    "lib/ocaml/buffer.cmti",
    "lib/ocaml/buffer.ml",
    "lib/ocaml/buffer.mli",
    "lib/ocaml/bytes.cmi",
    "lib/ocaml/bytes.cmj",
    "lib/ocaml/bytes.cmt",
    "lib/ocaml/bytes.cmti",
    "lib/ocaml/bytes.ml",
    "lib/ocaml/bytes.mli",
    "lib/ocaml/bytesLabels.cmi",
    "lib/ocaml/bytesLabels.cmj",
    "lib/ocaml/bytesLabels.cmt",
    "lib/ocaml/bytesLabels.cmti",
    "lib/ocaml/bytesLabels.ml",
    "lib/ocaml/bytesLabels.mli",
    "lib/ocaml/callback.cmi",
    "lib/ocaml/callback.cmj",
    "lib/ocaml/callback.cmt",
    "lib/ocaml/callback.cmti",
    "lib/ocaml/callback.ml",
    "lib/ocaml/callback.mli",
    "lib/ocaml/caml_array.cmj",
    "lib/ocaml/caml_array.cmt",
    "lib/ocaml/caml_array.cmti",
    "lib/ocaml/caml_backtrace.cmj",
    "lib/ocaml/caml_backtrace.cmt",
    "lib/ocaml/caml_backtrace.cmti",
    "lib/ocaml/caml_basic.cmj",
    "lib/ocaml/caml_basic.cmt",
    "lib/ocaml/caml_basic.cmti",
    "lib/ocaml/caml_builtin_exceptions.cmj",
    "lib/ocaml/caml_builtin_exceptions.cmt",
    "lib/ocaml/caml_builtin_exceptions.cmti",
    "lib/ocaml/caml_bytes.cmj",
    "lib/ocaml/caml_bytes.cmt",
    "lib/ocaml/caml_bytes.cmti",
    "lib/ocaml/caml_exceptions.cmi",
    "lib/ocaml/caml_exceptions.cmj",
    "lib/ocaml/caml_exceptions.cmt",
    "lib/ocaml/caml_exceptions.cmti",
    "lib/ocaml/caml_exceptions.ml",
    "lib/ocaml/caml_exceptions.mli",
    "lib/ocaml/caml_float.cmj",
    "lib/ocaml/caml_float.cmt",
    "lib/ocaml/caml_float.cmti",
    "lib/ocaml/caml_format.cmj",
    "lib/ocaml/caml_format.cmt",
    "lib/ocaml/caml_format.cmti",
    "lib/ocaml/caml_gc.cmj",
    "lib/ocaml/caml_gc.cmt",
    "lib/ocaml/caml_gc.cmti",
    "lib/ocaml/caml_hash.cmj",
    "lib/ocaml/caml_hash.cmt",
    "lib/ocaml/caml_hash.cmti",
    "lib/ocaml/caml_hash_primitive.cmj",
    "lib/ocaml/caml_hash_primitive.cmt",
    "lib/ocaml/caml_hash_primitive.cmti",
    "lib/ocaml/caml_int32.cmj",
    "lib/ocaml/caml_int32.cmt",
    "lib/ocaml/caml_int32.cmti",
    "lib/ocaml/caml_int64.cmj",
    "lib/ocaml/caml_int64.cmt",
    "lib/ocaml/caml_int64.cmti",
    "lib/ocaml/caml_io.cmj",
    "lib/ocaml/caml_io.cmt",
    "lib/ocaml/caml_lexer.cmj",
    "lib/ocaml/caml_lexer.cmt",
    "lib/ocaml/caml_lexer.cmti",
    "lib/ocaml/caml_md5.cmj",
    "lib/ocaml/caml_md5.cmt",
    "lib/ocaml/caml_md5.cmti",
    "lib/ocaml/caml_missing_polyfill.cmj",
    "lib/ocaml/caml_missing_polyfill.cmt",
    "lib/ocaml/caml_missing_polyfill.cmti",
    "lib/ocaml/caml_module.cmj",
    "lib/ocaml/caml_module.cmt",
    "lib/ocaml/caml_obj.cmj",
    "lib/ocaml/caml_obj.cmt",
    "lib/ocaml/caml_obj.cmti",
    "lib/ocaml/caml_oo.cmj",
    "lib/ocaml/caml_oo.cmt",
    "lib/ocaml/caml_oo.cmti",
    "lib/ocaml/caml_oo_curry.cmj",
    "lib/ocaml/caml_oo_curry.cmt",
    "lib/ocaml/caml_parser.cmj",
    "lib/ocaml/caml_parser.cmt",
    "lib/ocaml/caml_parser.cmti",
    "lib/ocaml/caml_primitive.cmj",
    "lib/ocaml/caml_primitive.cmt",
    "lib/ocaml/caml_primitive.cmti",
    "lib/ocaml/caml_queue.cmj",
    "lib/ocaml/caml_queue.cmt",
    "lib/ocaml/caml_queue.cmti",
    "lib/ocaml/caml_string.cmj",
    "lib/ocaml/caml_string.cmt",
    "lib/ocaml/caml_string.cmti",
    "lib/ocaml/caml_sys.cmj",
    "lib/ocaml/caml_sys.cmt",
    "lib/ocaml/caml_sys.cmti",
    "lib/ocaml/caml_utils.cmj",
    "lib/ocaml/caml_utils.cmt",
    "lib/ocaml/caml_utils.cmti",
    "lib/ocaml/caml_weak.cmj",
    "lib/ocaml/caml_weak.cmt",
    "lib/ocaml/caml_weak.cmti",
    "lib/ocaml/camlinternalFormat.cmi",
    "lib/ocaml/camlinternalFormat.cmj",
    "lib/ocaml/camlinternalFormat.cmt",
    "lib/ocaml/camlinternalFormat.cmti",
    "lib/ocaml/camlinternalFormat.ml",
    "lib/ocaml/camlinternalFormat.mli",
    "lib/ocaml/camlinternalFormatBasics.cmi",
    "lib/ocaml/camlinternalFormatBasics.cmj",
    "lib/ocaml/camlinternalFormatBasics.cmt",
    "lib/ocaml/camlinternalFormatBasics.cmti",
    "lib/ocaml/camlinternalFormatBasics.ml",
    "lib/ocaml/camlinternalFormatBasics.mli",
    "lib/ocaml/camlinternalLazy.cmi",
    "lib/ocaml/camlinternalLazy.cmj",
    "lib/ocaml/camlinternalLazy.cmt",
    "lib/ocaml/camlinternalLazy.cmti",
    "lib/ocaml/camlinternalLazy.ml",
    "lib/ocaml/camlinternalLazy.mli",
    "lib/ocaml/camlinternalMod.cmi",
    "lib/ocaml/camlinternalMod.cmj",
    "lib/ocaml/camlinternalMod.cmt",
    "lib/ocaml/camlinternalMod.cmti",
    "lib/ocaml/camlinternalMod.ml",
    "lib/ocaml/camlinternalMod.mli",
    "lib/ocaml/camlinternalOO.cmi",
    "lib/ocaml/camlinternalOO.cmj",
    "lib/ocaml/camlinternalOO.cmt",
    "lib/ocaml/camlinternalOO.cmti",
    "lib/ocaml/camlinternalOO.ml",
    "lib/ocaml/camlinternalOO.mli",
    "lib/ocaml/char.cmi",
    "lib/ocaml/char.cmj",
    "lib/ocaml/char.cmt",
    "lib/ocaml/char.cmti",
    "lib/ocaml/char.ml",
    "lib/ocaml/char.mli",
    "lib/ocaml/complex.cmi",
    "lib/ocaml/complex.cmj",
    "lib/ocaml/complex.cmt",
    "lib/ocaml/complex.cmti",
    "lib/ocaml/complex.ml",
    "lib/ocaml/complex.mli",
    "lib/ocaml/curry.cmj",
    "lib/ocaml/curry.cmt",
    "lib/ocaml/digest.cmi",
    "lib/ocaml/digest.cmj",
    "lib/ocaml/digest.cmt",
    "lib/ocaml/digest.cmti",
    "lib/ocaml/digest.ml",
    "lib/ocaml/digest.mli",
    "lib/ocaml/dom.cmi",
    "lib/ocaml/dom.cmti",
    "lib/ocaml/dom.mli",
    "lib/ocaml/dom_storage.cmi",
    "lib/ocaml/dom_storage.cmti",
    "lib/ocaml/dom_storage.mli",
    "lib/ocaml/filename.cmi",
    "lib/ocaml/filename.cmj",
    "lib/ocaml/filename.cmt",
    "lib/ocaml/filename.cmti",
    "lib/ocaml/filename.ml",
    "lib/ocaml/filename.mli",
    "lib/ocaml/format.cmi",
    "lib/ocaml/format.cmj",
    "lib/ocaml/format.cmt",
    "lib/ocaml/format.cmti",
    "lib/ocaml/format.ml",
    "lib/ocaml/format.mli",
    "lib/ocaml/gc.cmi",
    "lib/ocaml/gc.cmj",
    "lib/ocaml/gc.cmt",
    "lib/ocaml/gc.cmti",
    "lib/ocaml/gc.ml",
    "lib/ocaml/gc.mli",
    "lib/ocaml/genlex.cmi",
    "lib/ocaml/genlex.cmj",
    "lib/ocaml/genlex.cmt",
    "lib/ocaml/genlex.cmti",
    "lib/ocaml/genlex.ml",
    "lib/ocaml/genlex.mli",
    "lib/ocaml/hashmap.cppo.ml",
    "lib/ocaml/hashmap.cppo.mli",
    "lib/ocaml/hashset.cppo.ml",
    "lib/ocaml/hashset.cppo.mli",
    "lib/ocaml/hashtbl.cmi",
    "lib/ocaml/hashtbl.cmj",
    "lib/ocaml/hashtbl.cmt",
    "lib/ocaml/hashtbl.cmti",
    "lib/ocaml/hashtbl.ml",
    "lib/ocaml/hashtbl.mli",
    "lib/ocaml/int32.cmi",
    "lib/ocaml/int32.cmj",
    "lib/ocaml/int32.cmt",
    "lib/ocaml/int32.cmti",
    "lib/ocaml/int32.ml",
    "lib/ocaml/int32.mli",
    "lib/ocaml/int64.cmi",
    "lib/ocaml/int64.cmj",
    "lib/ocaml/int64.cmt",
    "lib/ocaml/int64.cmti",
    "lib/ocaml/int64.ml",
    "lib/ocaml/int64.mli",
    "lib/ocaml/internal_map.cppo.ml",
    "lib/ocaml/internal_set.cppo.ml",
    "lib/ocaml/js.cmi",
    "lib/ocaml/js.cmj",
    "lib/ocaml/js.cmt",
    "lib/ocaml/js.cmti",
    "lib/ocaml/js.ml",
    "lib/ocaml/js_array.cmi",
    "lib/ocaml/js_array.cmj",
    "lib/ocaml/js_array.cmt",
    "lib/ocaml/js_array.ml",
    "lib/ocaml/js_cast.cmi",
    "lib/ocaml/js_cast.cmj",
    "lib/ocaml/js_cast.cmt",
    "lib/ocaml/js_cast.cmti",
    "lib/ocaml/js_cast.ml",
    "lib/ocaml/js_cast.mli",
    "lib/ocaml/js_console.cmi",
    "lib/ocaml/js_console.cmj",
    "lib/ocaml/js_console.cmt",
    "lib/ocaml/js_console.ml",
    "lib/ocaml/js_date.cmi",
    "lib/ocaml/js_date.cmj",
    "lib/ocaml/js_date.cmt",
    "lib/ocaml/js_date.ml",
    "lib/ocaml/js_dict.cmi",
    "lib/ocaml/js_dict.cmj",
    "lib/ocaml/js_dict.cmt",
    "lib/ocaml/js_dict.cmti",
    "lib/ocaml/js_dict.ml",
    "lib/ocaml/js_dict.mli",
    "lib/ocaml/js_exn.cmi",
    "lib/ocaml/js_exn.cmj",
    "lib/ocaml/js_exn.cmt",
    "lib/ocaml/js_exn.cmti",
    "lib/ocaml/js_exn.ml",
    "lib/ocaml/js_exn.mli",
    "lib/ocaml/js_float.cmi",
    "lib/ocaml/js_float.cmj",
    "lib/ocaml/js_float.cmt",
    "lib/ocaml/js_float.ml",
    "lib/ocaml/js_global.cmi",
    "lib/ocaml/js_global.cmj",
    "lib/ocaml/js_global.cmt",
    "lib/ocaml/js_global.ml",
    "lib/ocaml/js_int.cmi",
    "lib/ocaml/js_int.cmj",
    "lib/ocaml/js_int.cmt",
    "lib/ocaml/js_int.ml",
    "lib/ocaml/js_int64.cmj",
    "lib/ocaml/js_int64.cmt",
    "lib/ocaml/js_internal.cmi",
    "lib/ocaml/js_internal.cmj",
    "lib/ocaml/js_internal.cmt",
    "lib/ocaml/js_internal.cmti",
    "lib/ocaml/js_json.cmi",
    "lib/ocaml/js_json.cmj",
    "lib/ocaml/js_json.cmt",
    "lib/ocaml/js_json.cmti",
    "lib/ocaml/js_json.ml",
    "lib/ocaml/js_json.mli",
    "lib/ocaml/js_list.cmi",
    "lib/ocaml/js_list.cmj",
    "lib/ocaml/js_list.cmt",
    "lib/ocaml/js_list.cmti",
    "lib/ocaml/js_list.ml",
    "lib/ocaml/js_list.mli",
    "lib/ocaml/js_mapperRt.cmi",
    "lib/ocaml/js_mapperRt.cmj",
    "lib/ocaml/js_mapperRt.cmt",
    "lib/ocaml/js_mapperRt.cmti",
    "lib/ocaml/js_mapperRt.ml",
    "lib/ocaml/js_mapperRt.mli",
    "lib/ocaml/js_math.cmi",
    "lib/ocaml/js_math.cmj",
    "lib/ocaml/js_math.cmt",
    "lib/ocaml/js_math.ml",
    "lib/ocaml/js_nativeint.cmj",
    "lib/ocaml/js_nativeint.cmt",
    "lib/ocaml/js_null.cmi",
    "lib/ocaml/js_null.cmj",
    "lib/ocaml/js_null.cmt",
    "lib/ocaml/js_null.cmti",
    "lib/ocaml/js_null.ml",
    "lib/ocaml/js_null_undefined.cmi",
    "lib/ocaml/js_null_undefined.cmj",
    "lib/ocaml/js_null_undefined.cmt",
    "lib/ocaml/js_null_undefined.cmti",
    "lib/ocaml/js_null_undefined.ml",
    "lib/ocaml/js_null_undefined.mli",
    "lib/ocaml/js_obj.cmi",
    "lib/ocaml/js_obj.cmj",
    "lib/ocaml/js_obj.cmt",
    "lib/ocaml/js_obj.ml",
    "lib/ocaml/js_option.cmi",
    "lib/ocaml/js_option.cmj",
    "lib/ocaml/js_option.cmt",
    "lib/ocaml/js_option.cmti",
    "lib/ocaml/js_option.ml",
    "lib/ocaml/js_option.mli",
    "lib/ocaml/js_primitive.cmj",
    "lib/ocaml/js_primitive.cmt",
    "lib/ocaml/js_primitive.cmti",
    "lib/ocaml/js_promise.cmi",
    "lib/ocaml/js_promise.cmj",
    "lib/ocaml/js_promise.cmt",
    "lib/ocaml/js_promise.ml",
    "lib/ocaml/js_re.cmi",
    "lib/ocaml/js_re.cmti",
    "lib/ocaml/js_re.mli",
    "lib/ocaml/js_result.cmi",
    "lib/ocaml/js_result.cmj",
    "lib/ocaml/js_result.cmt",
    "lib/ocaml/js_result.cmti",
    "lib/ocaml/js_result.ml",
    "lib/ocaml/js_result.mli",
    "lib/ocaml/js_string.cmi",
    "lib/ocaml/js_string.cmj",
    "lib/ocaml/js_string.cmt",
    "lib/ocaml/js_string.ml",
    "lib/ocaml/js_typed_array.cmi",
    "lib/ocaml/js_typed_array.cmj",
    "lib/ocaml/js_typed_array.cmt",
    "lib/ocaml/js_typed_array.ml",
    "lib/ocaml/js_types.cmi",
    "lib/ocaml/js_types.cmj",
    "lib/ocaml/js_types.cmt",
    "lib/ocaml/js_types.cmti",
    "lib/ocaml/js_types.ml",
    "lib/ocaml/js_types.mli",
    "lib/ocaml/js_undefined.cmi",
    "lib/ocaml/js_undefined.cmj",
    "lib/ocaml/js_undefined.cmt",
    "lib/ocaml/js_undefined.cmti",
    "lib/ocaml/js_undefined.ml",
    "lib/ocaml/js_unsafe.cmi",
    "lib/ocaml/js_unsafe.cmj",
    "lib/ocaml/js_unsafe.cmt",
    "lib/ocaml/js_unsafe.cmti",
    "lib/ocaml/js_vector.cmi",
    "lib/ocaml/js_vector.cmj",
    "lib/ocaml/js_vector.cmt",
    "lib/ocaml/js_vector.cmti",
    "lib/ocaml/js_vector.ml",
    "lib/ocaml/js_vector.mli",
    "lib/ocaml/lazy.cmi",
    "lib/ocaml/lazy.cmj",
    "lib/ocaml/lazy.cmt",
    "lib/ocaml/lazy.cmti",
    "lib/ocaml/lazy.ml",
    "lib/ocaml/lazy.mli",
    "lib/ocaml/lexing.cmi",
    "lib/ocaml/lexing.cmj",
    "lib/ocaml/lexing.cmt",
    "lib/ocaml/lexing.cmti",
    "lib/ocaml/lexing.ml",
    "lib/ocaml/lexing.mli",
    "lib/ocaml/list.cmi",
    "lib/ocaml/list.cmj",
    "lib/ocaml/list.cmt",
    "lib/ocaml/list.cmti",
    "lib/ocaml/list.ml",
    "lib/ocaml/list.mli",
    "lib/ocaml/listLabels.cmi",
    "lib/ocaml/listLabels.cmj",
    "lib/ocaml/listLabels.cmt",
    "lib/ocaml/listLabels.cmti",
    "lib/ocaml/listLabels.ml",
    "lib/ocaml/listLabels.mli",
    "lib/ocaml/map.cmi",
    "lib/ocaml/map.cmj",
    "lib/ocaml/map.cmt",
    "lib/ocaml/map.cmti",
    "lib/ocaml/map.cppo.ml",
    "lib/ocaml/map.cppo.mli",
    "lib/ocaml/map.ml",
    "lib/ocaml/map.mli",
    "lib/ocaml/mapm.cppo.ml",
    "lib/ocaml/mapm.cppo.mli",
    "lib/ocaml/marshal.cmi",
    "lib/ocaml/marshal.cmj",
    "lib/ocaml/marshal.cmt",
    "lib/ocaml/marshal.cmti",
    "lib/ocaml/marshal.ml",
    "lib/ocaml/marshal.mli",
    "lib/ocaml/moreLabels.cmi",
    "lib/ocaml/moreLabels.cmj",
    "lib/ocaml/moreLabels.cmt",
    "lib/ocaml/moreLabels.cmti",
    "lib/ocaml/moreLabels.ml",
    "lib/ocaml/moreLabels.mli",
    "lib/ocaml/nativeint.cmi",
    "lib/ocaml/nativeint.cmj",
    "lib/ocaml/nativeint.cmt",
    "lib/ocaml/nativeint.cmti",
    "lib/ocaml/nativeint.ml",
    "lib/ocaml/nativeint.mli",
    "lib/ocaml/node.cmi",
    "lib/ocaml/node.cmj",
    "lib/ocaml/node.cmt",
    "lib/ocaml/node.ml",
    "lib/ocaml/node_buffer.cmi",
    "lib/ocaml/node_buffer.cmj",
    "lib/ocaml/node_buffer.cmt",
    "lib/ocaml/node_buffer.ml",
    "lib/ocaml/node_child_process.cmi",
    "lib/ocaml/node_child_process.cmj",
    "lib/ocaml/node_child_process.cmt",
    "lib/ocaml/node_child_process.ml",
    "lib/ocaml/node_fs.cmi",
    "lib/ocaml/node_fs.cmj",
    "lib/ocaml/node_fs.cmt",
    "lib/ocaml/node_fs.ml",
    "lib/ocaml/node_module.cmi",
    "lib/ocaml/node_module.cmj",
    "lib/ocaml/node_module.cmt",
    "lib/ocaml/node_module.ml",
    "lib/ocaml/node_path.cmi",
    "lib/ocaml/node_path.cmj",
    "lib/ocaml/node_path.cmt",
    "lib/ocaml/node_path.ml",
    "lib/ocaml/node_process.cmi",
    "lib/ocaml/node_process.cmj",
    "lib/ocaml/node_process.cmt",
    "lib/ocaml/node_process.cmti",
    "lib/ocaml/node_process.ml",
    "lib/ocaml/node_process.mli",
    "lib/ocaml/obj.cmi",
    "lib/ocaml/obj.cmj",
    "lib/ocaml/obj.cmt",
    "lib/ocaml/obj.cmti",
    "lib/ocaml/obj.ml",
    "lib/ocaml/obj.mli",
    "lib/ocaml/oo.cmi",
    "lib/ocaml/oo.cmj",
    "lib/ocaml/oo.cmt",
    "lib/ocaml/oo.cmti",
    "lib/ocaml/oo.ml",
    "lib/ocaml/oo.mli",
    "lib/ocaml/parsing.cmi",
    "lib/ocaml/parsing.cmj",
    "lib/ocaml/parsing.cmt",
    "lib/ocaml/parsing.cmti",
    "lib/ocaml/parsing.ml",
    "lib/ocaml/parsing.mli",
    "lib/ocaml/pervasives.cmi",
    "lib/ocaml/pervasives.cmj",
    "lib/ocaml/pervasives.cmt",
    "lib/ocaml/pervasives.cmti",
    "lib/ocaml/pervasives.ml",
    "lib/ocaml/pervasives.mli",
    "lib/ocaml/printexc.cmi",
    "lib/ocaml/printexc.cmj",
    "lib/ocaml/printexc.cmt",
    "lib/ocaml/printexc.cmti",
    "lib/ocaml/printexc.ml",
    "lib/ocaml/printexc.mli",
    "lib/ocaml/printf.cmi",
    "lib/ocaml/printf.cmj",
    "lib/ocaml/printf.cmt",
    "lib/ocaml/printf.cmti",
    "lib/ocaml/printf.ml",
    "lib/ocaml/printf.mli",
    "lib/ocaml/queue.cmi",
    "lib/ocaml/queue.cmj",
    "lib/ocaml/queue.cmt",
    "lib/ocaml/queue.cmti",
    "lib/ocaml/queue.ml",
    "lib/ocaml/queue.mli",
    "lib/ocaml/random.cmi",
    "lib/ocaml/random.cmj",
    "lib/ocaml/random.cmt",
    "lib/ocaml/random.cmti",
    "lib/ocaml/random.ml",
    "lib/ocaml/random.mli",
    "lib/ocaml/scanf.cmi",
    "lib/ocaml/scanf.cmj",
    "lib/ocaml/scanf.cmt",
    "lib/ocaml/scanf.cmti",
    "lib/ocaml/scanf.ml",
    "lib/ocaml/scanf.mli",
    "lib/ocaml/set.cmi",
    "lib/ocaml/set.cmj",
    "lib/ocaml/set.cmt",
    "lib/ocaml/set.cmti",
    "lib/ocaml/set.cppo.ml",
    "lib/ocaml/set.cppo.mli",
    "lib/ocaml/set.ml",
    "lib/ocaml/set.mli",
    "lib/ocaml/setm.cppo.ml",
    "lib/ocaml/setm.cppo.mli",
    "lib/ocaml/sort.cmi",
    "lib/ocaml/sort.cmj",
    "lib/ocaml/sort.cmt",
    "lib/ocaml/sort.cmti",
    "lib/ocaml/sort.cppo.ml",
    "lib/ocaml/sort.cppo.mli",
    "lib/ocaml/sort.ml",
    "lib/ocaml/sort.mli",
    "lib/ocaml/stack.cmi",
    "lib/ocaml/stack.cmj",
    "lib/ocaml/stack.cmt",
    "lib/ocaml/stack.cmti",
    "lib/ocaml/stack.ml",
    "lib/ocaml/stack.mli",
    "lib/ocaml/stdLabels.cmi",
    "lib/ocaml/stdLabels.cmj",
    "lib/ocaml/stdLabels.cmt",
    "lib/ocaml/stdLabels.cmti",
    "lib/ocaml/stdLabels.ml",
    "lib/ocaml/stdLabels.mli",
    "lib/ocaml/std_exit.cmi",
    "lib/ocaml/std_exit.cmj",
    "lib/ocaml/std_exit.cmt",
    "lib/ocaml/std_exit.ml",
    "lib/ocaml/stream.cmi",
    "lib/ocaml/stream.cmj",
    "lib/ocaml/stream.cmt",
    "lib/ocaml/stream.cmti",
    "lib/ocaml/stream.ml",
    "lib/ocaml/stream.mli",
    "lib/ocaml/string.cmi",
    "lib/ocaml/string.cmj",
    "lib/ocaml/string.cmt",
    "lib/ocaml/string.cmti",
    "lib/ocaml/string.ml",
    "lib/ocaml/string.mli",
    "lib/ocaml/stringLabels.cmi",
    "lib/ocaml/stringLabels.cmj",
    "lib/ocaml/stringLabels.cmt",
    "lib/ocaml/stringLabels.cmti",
    "lib/ocaml/stringLabels.ml",
    "lib/ocaml/stringLabels.mli",
    "lib/ocaml/sys.cmi",
    "lib/ocaml/sys.cmj",
    "lib/ocaml/sys.cmt",
    "lib/ocaml/sys.cmti",
    "lib/ocaml/sys.ml",
    "lib/ocaml/sys.mli",
    "lib/ocaml/unix.cmi",
    "lib/ocaml/unix.cmj",
    "lib/ocaml/unix.cmt",
    "lib/ocaml/unix.cmti",
    "lib/ocaml/unix.ml",
    "lib/ocaml/unix.mli",
    "lib/ocaml/unixLabels.cmi",
    "lib/ocaml/unixLabels.cmj",
    "lib/ocaml/unixLabels.cmt",
    "lib/ocaml/unixLabels.cmti",
    "lib/ocaml/unixLabels.ml",
    "lib/ocaml/unixLabels.mli",
    "lib/ocaml/weak.cmi",
    "lib/ocaml/weak.cmj",
    "lib/ocaml/weak.cmt",
    "lib/ocaml/weak.cmti",
    "lib/ocaml/weak.ml",
    "lib/ocaml/weak.mli",
]

unpack_filegroup(
    name = "stdlib.ml",
    files = ml_files,
    tar = ":stdlib.ml.tar",
)
