package(default_visibility = ["//:__subpackages__"])

load("//reason/private:utils.bzl", "unpack_filegroup")

ml_files = [
    "lib/ocaml/arg.cmi",
    "lib/ocaml/arg.cmt",
    "lib/ocaml/arg.cmti",
    "lib/ocaml/arg.cmx",
    "lib/ocaml/arg.ml",
    "lib/ocaml/arg.mli",
    "lib/ocaml/arg.p.cmt",
    "lib/ocaml/arg.p.cmx",
    "lib/ocaml/arith_flags.cmx",
    "lib/ocaml/arith_status.cmi",
    "lib/ocaml/arith_status.cmx",
    "lib/ocaml/arith_status.mli",
    "lib/ocaml/array.cmi",
    "lib/ocaml/array.cmt",
    "lib/ocaml/array.cmti",
    "lib/ocaml/array.cmx",
    "lib/ocaml/array.ml",
    "lib/ocaml/array.mli",
    "lib/ocaml/array.p.cmt",
    "lib/ocaml/array.p.cmx",
    "lib/ocaml/arrayLabels.cmi",
    "lib/ocaml/arrayLabels.cmt",
    "lib/ocaml/arrayLabels.cmti",
    "lib/ocaml/arrayLabels.cmx",
    "lib/ocaml/arrayLabels.ml",
    "lib/ocaml/arrayLabels.mli",
    "lib/ocaml/arrayLabels.p.cmt",
    "lib/ocaml/arrayLabels.p.cmx",
    "lib/ocaml/big_int.cmi",
    "lib/ocaml/big_int.cmx",
    "lib/ocaml/big_int.mli",
    "lib/ocaml/bigarray.a",
    "lib/ocaml/bigarray.cma",
    "lib/ocaml/bigarray.cmi",
    "lib/ocaml/bigarray.cmx",
    "lib/ocaml/bigarray.cmxa",
    "lib/ocaml/bigarray.cmxs",
    "lib/ocaml/bigarray.mli",
    "lib/ocaml/buffer.cmi",
    "lib/ocaml/buffer.cmt",
    "lib/ocaml/buffer.cmti",
    "lib/ocaml/buffer.cmx",
    "lib/ocaml/buffer.ml",
    "lib/ocaml/buffer.mli",
    "lib/ocaml/buffer.p.cmt",
    "lib/ocaml/buffer.p.cmx",
    "lib/ocaml/bytes.cmi",
    "lib/ocaml/bytes.cmt",
    "lib/ocaml/bytes.cmti",
    "lib/ocaml/bytes.cmx",
    "lib/ocaml/bytes.ml",
    "lib/ocaml/bytes.mli",
    "lib/ocaml/bytes.p.cmt",
    "lib/ocaml/bytes.p.cmx",
    "lib/ocaml/bytesLabels.cmi",
    "lib/ocaml/bytesLabels.cmt",
    "lib/ocaml/bytesLabels.cmti",
    "lib/ocaml/bytesLabels.cmx",
    "lib/ocaml/bytesLabels.ml",
    "lib/ocaml/bytesLabels.mli",
    "lib/ocaml/bytesLabels.p.cmt",
    "lib/ocaml/bytesLabels.p.cmx",
    "lib/ocaml/callback.cmi",
    "lib/ocaml/callback.cmt",
    "lib/ocaml/callback.cmti",
    "lib/ocaml/callback.cmx",
    "lib/ocaml/callback.ml",
    "lib/ocaml/callback.mli",
    "lib/ocaml/callback.p.cmt",
    "lib/ocaml/callback.p.cmx",
    "lib/ocaml/caml",
    "lib/ocaml/camlheader",
    "lib/ocaml/camlheader_ur",
    "lib/ocaml/camlinternalFormat.cmi",
    "lib/ocaml/camlinternalFormat.cmt",
    "lib/ocaml/camlinternalFormat.cmti",
    "lib/ocaml/camlinternalFormat.cmx",
    "lib/ocaml/camlinternalFormat.ml",
    "lib/ocaml/camlinternalFormat.mli",
    "lib/ocaml/camlinternalFormat.p.cmt",
    "lib/ocaml/camlinternalFormat.p.cmx",
    "lib/ocaml/camlinternalFormatBasics.cmi",
    "lib/ocaml/camlinternalFormatBasics.cmt",
    "lib/ocaml/camlinternalFormatBasics.cmti",
    "lib/ocaml/camlinternalFormatBasics.cmx",
    "lib/ocaml/camlinternalFormatBasics.ml",
    "lib/ocaml/camlinternalFormatBasics.mli",
    "lib/ocaml/camlinternalFormatBasics.p.cmt",
    "lib/ocaml/camlinternalFormatBasics.p.cmx",
    "lib/ocaml/camlinternalLazy.cmi",
    "lib/ocaml/camlinternalLazy.cmt",
    "lib/ocaml/camlinternalLazy.cmti",
    "lib/ocaml/camlinternalLazy.cmx",
    "lib/ocaml/camlinternalLazy.ml",
    "lib/ocaml/camlinternalLazy.mli",
    "lib/ocaml/camlinternalLazy.p.cmt",
    "lib/ocaml/camlinternalLazy.p.cmx",
    "lib/ocaml/camlinternalMod.cmi",
    "lib/ocaml/camlinternalMod.cmt",
    "lib/ocaml/camlinternalMod.cmti",
    "lib/ocaml/camlinternalMod.cmx",
    "lib/ocaml/camlinternalMod.ml",
    "lib/ocaml/camlinternalMod.mli",
    "lib/ocaml/camlinternalMod.p.cmt",
    "lib/ocaml/camlinternalMod.p.cmx",
    "lib/ocaml/camlinternalOO.cmi",
    "lib/ocaml/camlinternalOO.cmt",
    "lib/ocaml/camlinternalOO.cmti",
    "lib/ocaml/camlinternalOO.cmx",
    "lib/ocaml/camlinternalOO.ml",
    "lib/ocaml/camlinternalOO.mli",
    "lib/ocaml/camlinternalOO.p.cmt",
    "lib/ocaml/camlinternalOO.p.cmx",
    "lib/ocaml/char.cmi",
    "lib/ocaml/char.cmt",
    "lib/ocaml/char.cmti",
    "lib/ocaml/char.cmx",
    "lib/ocaml/char.ml",
    "lib/ocaml/char.mli",
    "lib/ocaml/char.p.cmt",
    "lib/ocaml/char.p.cmx",
    "lib/ocaml/compiler-libs",
    "lib/ocaml/complex.cmi",
    "lib/ocaml/complex.cmt",
    "lib/ocaml/complex.cmti",
    "lib/ocaml/complex.cmx",
    "lib/ocaml/complex.ml",
    "lib/ocaml/complex.mli",
    "lib/ocaml/complex.p.cmt",
    "lib/ocaml/complex.p.cmx",
    "lib/ocaml/condition.mli",
    "lib/ocaml/digest.cmi",
    "lib/ocaml/digest.cmt",
    "lib/ocaml/digest.cmti",
    "lib/ocaml/digest.cmx",
    "lib/ocaml/digest.ml",
    "lib/ocaml/digest.mli",
    "lib/ocaml/digest.p.cmt",
    "lib/ocaml/digest.p.cmx",
    "lib/ocaml/dynlink.a",
    "lib/ocaml/dynlink.cma",
    "lib/ocaml/dynlink.cmi",
    "lib/ocaml/dynlink.cmx",
    "lib/ocaml/dynlink.cmxa",
    "lib/ocaml/dynlink.mli",
    "lib/ocaml/ephemeron.cmi",
    "lib/ocaml/ephemeron.cmt",
    "lib/ocaml/ephemeron.cmti",
    "lib/ocaml/ephemeron.cmx",
    "lib/ocaml/ephemeron.ml",
    "lib/ocaml/ephemeron.mli",
    "lib/ocaml/ephemeron.p.cmt",
    "lib/ocaml/ephemeron.p.cmx",
    "lib/ocaml/event.mli",
    "lib/ocaml/expunge",
    "lib/ocaml/extract_crc",
    "lib/ocaml/filename.cmi",
    "lib/ocaml/filename.cmt",
    "lib/ocaml/filename.cmti",
    "lib/ocaml/filename.cmx",
    "lib/ocaml/filename.ml",
    "lib/ocaml/filename.mli",
    "lib/ocaml/filename.p.cmt",
    "lib/ocaml/filename.p.cmx",
    "lib/ocaml/format.cmi",
    "lib/ocaml/format.cmt",
    "lib/ocaml/format.cmti",
    "lib/ocaml/format.cmx",
    "lib/ocaml/format.ml",
    "lib/ocaml/format.mli",
    "lib/ocaml/format.p.cmt",
    "lib/ocaml/format.p.cmx",
    "lib/ocaml/gc.cmi",
    "lib/ocaml/gc.cmt",
    "lib/ocaml/gc.cmti",
    "lib/ocaml/gc.cmx",
    "lib/ocaml/gc.ml",
    "lib/ocaml/gc.mli",
    "lib/ocaml/gc.p.cmt",
    "lib/ocaml/gc.p.cmx",
    "lib/ocaml/genlex.cmi",
    "lib/ocaml/genlex.cmt",
    "lib/ocaml/genlex.cmti",
    "lib/ocaml/genlex.cmx",
    "lib/ocaml/genlex.ml",
    "lib/ocaml/genlex.mli",
    "lib/ocaml/genlex.p.cmt",
    "lib/ocaml/genlex.p.cmx",
    "lib/ocaml/hashtbl.cmi",
    "lib/ocaml/hashtbl.cmt",
    "lib/ocaml/hashtbl.cmti",
    "lib/ocaml/hashtbl.cmx",
    "lib/ocaml/hashtbl.ml",
    "lib/ocaml/hashtbl.mli",
    "lib/ocaml/hashtbl.p.cmt",
    "lib/ocaml/hashtbl.p.cmx",
    "lib/ocaml/int32.cmi",
    "lib/ocaml/int32.cmt",
    "lib/ocaml/int32.cmti",
    "lib/ocaml/int32.cmx",
    "lib/ocaml/int32.ml",
    "lib/ocaml/int32.mli",
    "lib/ocaml/int32.p.cmt",
    "lib/ocaml/int32.p.cmx",
    "lib/ocaml/int64.cmi",
    "lib/ocaml/int64.cmt",
    "lib/ocaml/int64.cmti",
    "lib/ocaml/int64.cmx",
    "lib/ocaml/int64.ml",
    "lib/ocaml/int64.mli",
    "lib/ocaml/int64.p.cmt",
    "lib/ocaml/int64.p.cmx",
    "lib/ocaml/int_misc.cmx",
    "lib/ocaml/lazy.cmi",
    "lib/ocaml/lazy.cmt",
    "lib/ocaml/lazy.cmti",
    "lib/ocaml/lazy.cmx",
    "lib/ocaml/lazy.ml",
    "lib/ocaml/lazy.mli",
    "lib/ocaml/lazy.p.cmt",
    "lib/ocaml/lazy.p.cmx",
    "lib/ocaml/ld.conf",
    "lib/ocaml/lexing.cmi",
    "lib/ocaml/lexing.cmt",
    "lib/ocaml/lexing.cmti",
    "lib/ocaml/lexing.cmx",
    "lib/ocaml/lexing.ml",
    "lib/ocaml/lexing.mli",
    "lib/ocaml/lexing.p.cmt",
    "lib/ocaml/lexing.p.cmx",
    "lib/ocaml/libasmrun.a",
    "lib/ocaml/libasmrun_pic.a",
    "lib/ocaml/libasmrun_shared.so",
    "lib/ocaml/libasmrunp.a",
    "lib/ocaml/libbigarray.a",
    "lib/ocaml/libcamlrun.a",
    "lib/ocaml/libcamlrun_pic.a",
    "lib/ocaml/libcamlrun_shared.so",
    "lib/ocaml/libcamlstr.a",
    "lib/ocaml/libnums.a",
    "lib/ocaml/libthreads.a",
    "lib/ocaml/libthreadsnat.a",
    "lib/ocaml/libunix.a",
    "lib/ocaml/list.cmi",
    "lib/ocaml/list.cmt",
    "lib/ocaml/list.cmti",
    "lib/ocaml/list.cmx",
    "lib/ocaml/list.ml",
    "lib/ocaml/list.mli",
    "lib/ocaml/list.p.cmt",
    "lib/ocaml/list.p.cmx",
    "lib/ocaml/listLabels.cmi",
    "lib/ocaml/listLabels.cmt",
    "lib/ocaml/listLabels.cmti",
    "lib/ocaml/listLabels.cmx",
    "lib/ocaml/listLabels.ml",
    "lib/ocaml/listLabels.mli",
    "lib/ocaml/listLabels.p.cmt",
    "lib/ocaml/listLabels.p.cmx",
    "lib/ocaml/map.cmi",
    "lib/ocaml/map.cmt",
    "lib/ocaml/map.cmti",
    "lib/ocaml/map.cmx",
    "lib/ocaml/map.ml",
    "lib/ocaml/map.mli",
    "lib/ocaml/map.p.cmt",
    "lib/ocaml/map.p.cmx",
    "lib/ocaml/marshal.cmi",
    "lib/ocaml/marshal.cmt",
    "lib/ocaml/marshal.cmti",
    "lib/ocaml/marshal.cmx",
    "lib/ocaml/marshal.ml",
    "lib/ocaml/marshal.mli",
    "lib/ocaml/marshal.p.cmt",
    "lib/ocaml/marshal.p.cmx",
    "lib/ocaml/moreLabels.cmi",
    "lib/ocaml/moreLabels.cmt",
    "lib/ocaml/moreLabels.cmti",
    "lib/ocaml/moreLabels.cmx",
    "lib/ocaml/moreLabels.ml",
    "lib/ocaml/moreLabels.mli",
    "lib/ocaml/moreLabels.p.cmt",
    "lib/ocaml/moreLabels.p.cmx",
    "lib/ocaml/mutex.mli",
    "lib/ocaml/nat.cmi",
    "lib/ocaml/nat.cmx",
    "lib/ocaml/nat.mli",
    "lib/ocaml/nativeint.cmi",
    "lib/ocaml/nativeint.cmt",
    "lib/ocaml/nativeint.cmti",
    "lib/ocaml/nativeint.cmx",
    "lib/ocaml/nativeint.ml",
    "lib/ocaml/nativeint.mli",
    "lib/ocaml/nativeint.p.cmt",
    "lib/ocaml/nativeint.p.cmx",
    "lib/ocaml/num.cmi",
    "lib/ocaml/num.cmx",
    "lib/ocaml/num.mli",
    "lib/ocaml/nums.a",
    "lib/ocaml/nums.cma",
    "lib/ocaml/nums.cmxa",
    "lib/ocaml/nums.cmxs",
    "lib/ocaml/obj.cmi",
    "lib/ocaml/obj.cmt",
    "lib/ocaml/obj.cmti",
    "lib/ocaml/obj.cmx",
    "lib/ocaml/obj.ml",
    "lib/ocaml/obj.mli",
    "lib/ocaml/obj.p.cmt",
    "lib/ocaml/obj.p.cmx",
    "lib/ocaml/objinfo_helper",
    "lib/ocaml/ocamldoc",
    "lib/ocaml/oo.cmi",
    "lib/ocaml/oo.cmt",
    "lib/ocaml/oo.cmti",
    "lib/ocaml/oo.cmx",
    "lib/ocaml/oo.ml",
    "lib/ocaml/oo.mli",
    "lib/ocaml/oo.p.cmt",
    "lib/ocaml/oo.p.cmx",
    "lib/ocaml/parsing.cmi",
    "lib/ocaml/parsing.cmt",
    "lib/ocaml/parsing.cmti",
    "lib/ocaml/parsing.cmx",
    "lib/ocaml/parsing.ml",
    "lib/ocaml/parsing.mli",
    "lib/ocaml/parsing.p.cmt",
    "lib/ocaml/parsing.p.cmx",
    "lib/ocaml/pervasives.cmi",
    "lib/ocaml/pervasives.cmt",
    "lib/ocaml/pervasives.cmti",
    "lib/ocaml/pervasives.cmx",
    "lib/ocaml/pervasives.ml",
    "lib/ocaml/pervasives.mli",
    "lib/ocaml/pervasives.p.cmt",
    "lib/ocaml/pervasives.p.cmx",
    "lib/ocaml/printexc.cmi",
    "lib/ocaml/printexc.cmt",
    "lib/ocaml/printexc.cmti",
    "lib/ocaml/printexc.cmx",
    "lib/ocaml/printexc.ml",
    "lib/ocaml/printexc.mli",
    "lib/ocaml/printexc.p.cmt",
    "lib/ocaml/printexc.p.cmx",
    "lib/ocaml/printf.cmi",
    "lib/ocaml/printf.cmt",
    "lib/ocaml/printf.cmti",
    "lib/ocaml/printf.cmx",
    "lib/ocaml/printf.ml",
    "lib/ocaml/printf.mli",
    "lib/ocaml/printf.p.cmt",
    "lib/ocaml/printf.p.cmx",
    "lib/ocaml/profiling.cmi",
    "lib/ocaml/profiling.cmo",
    "lib/ocaml/profiling.cmx",
    "lib/ocaml/profiling.o",
    "lib/ocaml/queue.cmi",
    "lib/ocaml/queue.cmt",
    "lib/ocaml/queue.cmti",
    "lib/ocaml/queue.cmx",
    "lib/ocaml/queue.ml",
    "lib/ocaml/queue.mli",
    "lib/ocaml/queue.p.cmt",
    "lib/ocaml/queue.p.cmx",
    "lib/ocaml/random.cmi",
    "lib/ocaml/random.cmt",
    "lib/ocaml/random.cmti",
    "lib/ocaml/random.cmx",
    "lib/ocaml/random.ml",
    "lib/ocaml/random.mli",
    "lib/ocaml/random.p.cmt",
    "lib/ocaml/random.p.cmx",
    "lib/ocaml/ratio.cmi",
    "lib/ocaml/ratio.cmx",
    "lib/ocaml/ratio.mli",
    "lib/ocaml/scanf.cmi",
    "lib/ocaml/scanf.cmt",
    "lib/ocaml/scanf.cmti",
    "lib/ocaml/scanf.cmx",
    "lib/ocaml/scanf.ml",
    "lib/ocaml/scanf.mli",
    "lib/ocaml/scanf.p.cmt",
    "lib/ocaml/scanf.p.cmx",
    "lib/ocaml/set.cmi",
    "lib/ocaml/set.cmt",
    "lib/ocaml/set.cmti",
    "lib/ocaml/set.cmx",
    "lib/ocaml/set.ml",
    "lib/ocaml/set.mli",
    "lib/ocaml/set.p.cmt",
    "lib/ocaml/set.p.cmx",
    "lib/ocaml/sort.cmi",
    "lib/ocaml/sort.cmt",
    "lib/ocaml/sort.cmti",
    "lib/ocaml/sort.cmx",
    "lib/ocaml/sort.ml",
    "lib/ocaml/sort.mli",
    "lib/ocaml/sort.p.cmt",
    "lib/ocaml/sort.p.cmx",
    "lib/ocaml/stack.cmi",
    "lib/ocaml/stack.cmt",
    "lib/ocaml/stack.cmti",
    "lib/ocaml/stack.cmx",
    "lib/ocaml/stack.ml",
    "lib/ocaml/stack.mli",
    "lib/ocaml/stack.p.cmt",
    "lib/ocaml/stack.p.cmx",
    "lib/ocaml/stdLabels.cmi",
    "lib/ocaml/stdLabels.cmt",
    "lib/ocaml/stdLabels.cmti",
    "lib/ocaml/stdLabels.cmx",
    "lib/ocaml/stdLabels.ml",
    "lib/ocaml/stdLabels.mli",
    "lib/ocaml/stdLabels.p.cmt",
    "lib/ocaml/stdLabels.p.cmx",
    "lib/ocaml/std_exit.cmi",
    "lib/ocaml/std_exit.cmo",
    "lib/ocaml/std_exit.cmt",
    "lib/ocaml/std_exit.cmx",
    "lib/ocaml/std_exit.ml",
    "lib/ocaml/std_exit.o",
    "lib/ocaml/std_exit.p.cmt",
    "lib/ocaml/std_exit.p.cmx",
    "lib/ocaml/std_exit.p.o",
    "lib/ocaml/stdlib.a",
    "lib/ocaml/stdlib.cma",
    "lib/ocaml/stdlib.cmxa",
    "lib/ocaml/stdlib.p.a",
    "lib/ocaml/stdlib.p.cmxa",
    "lib/ocaml/str.a",
    "lib/ocaml/str.cma",
    "lib/ocaml/str.cmi",
    "lib/ocaml/str.cmx",
    "lib/ocaml/str.cmxa",
    "lib/ocaml/str.cmxs",
    "lib/ocaml/str.mli",
    "lib/ocaml/stream.cmi",
    "lib/ocaml/stream.cmt",
    "lib/ocaml/stream.cmti",
    "lib/ocaml/stream.cmx",
    "lib/ocaml/stream.ml",
    "lib/ocaml/stream.mli",
    "lib/ocaml/stream.p.cmt",
    "lib/ocaml/stream.p.cmx",
    "lib/ocaml/string.cmi",
    "lib/ocaml/string.cmt",
    "lib/ocaml/string.cmti",
    "lib/ocaml/string.cmx",
    "lib/ocaml/string.ml",
    "lib/ocaml/string.mli",
    "lib/ocaml/string.p.cmt",
    "lib/ocaml/string.p.cmx",
    "lib/ocaml/stringLabels.cmi",
    "lib/ocaml/stringLabels.cmt",
    "lib/ocaml/stringLabels.cmti",
    "lib/ocaml/stringLabels.cmx",
    "lib/ocaml/stringLabels.ml",
    "lib/ocaml/stringLabels.mli",
    "lib/ocaml/stringLabels.p.cmt",
    "lib/ocaml/stringLabels.p.cmx",
    "lib/ocaml/stublibs",
    "lib/ocaml/sys.cmi",
    "lib/ocaml/sys.cmt",
    "lib/ocaml/sys.cmti",
    "lib/ocaml/sys.cmx",
    "lib/ocaml/sys.ml",
    "lib/ocaml/sys.mli",
    "lib/ocaml/sys.p.cmt",
    "lib/ocaml/sys.p.cmx",
    "lib/ocaml/thread.mli",
    "lib/ocaml/threadUnix.mli",
    "lib/ocaml/threads",
    "lib/ocaml/topdirs.cmi",
    "lib/ocaml/uchar.cmi",
    "lib/ocaml/uchar.cmt",
    "lib/ocaml/uchar.cmti",
    "lib/ocaml/uchar.cmx",
    "lib/ocaml/uchar.ml",
    "lib/ocaml/uchar.mli",
    "lib/ocaml/uchar.p.cmt",
    "lib/ocaml/uchar.p.cmx",
    "lib/ocaml/unix.a",
    "lib/ocaml/unix.cma",
    "lib/ocaml/unix.cmi",
    "lib/ocaml/unix.cmx",
    "lib/ocaml/unix.cmxa",
    "lib/ocaml/unix.cmxs",
    "lib/ocaml/unix.mli",
    "lib/ocaml/unixLabels.cmi",
    "lib/ocaml/unixLabels.cmx",
    "lib/ocaml/unixLabels.mli",
    "lib/ocaml/vmthreads",
    "lib/ocaml/weak.cmi",
    "lib/ocaml/weak.cmt",
    "lib/ocaml/weak.cmti",
    "lib/ocaml/weak.cmx",
    "lib/ocaml/weak.ml",
    "lib/ocaml/weak.mli",
    "lib/ocaml/weak.p.cmt",
    "lib/ocaml/weak.p.cmx",
]

unpack_filegroup(
    name = "stdlib.ml",
    files = ml_files,
    tar = "//reason/private/opam:ocaml_stdlib.tar",
)
