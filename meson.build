subdir('crengine')
subdir('thirdparty/antiword')
subdir('thirdparty/chmlib')

crengine_dependencies = [
  freetype_dep,
  fribidi_dep,
  harfbuzz_dep,
  jpeg_dep,
  lunasvg_dep,
  png_dep,
  srell_dep,
  unibreak_dep,
  utf8proc_dep,
  webpdemux_dep,
  zlib_dep,
  zstd_dep,
  ]

if get_option('debug')
  debug_flags = ['-D_DEBUG=1', '-DDEBUG=1']
else
  debug_flags = []
endif

antiword_lib = static_library('antiword',
  c_args: debug_flags + antiword_flags,
  include_directories: antiword_includes,
  sources: antiword_sources,
  )

chmlib_lib = static_library('chmlib',
  c_args: debug_flags + chmlib_flags,
  include_directories: chmlib_includes,
  sources: chmlib_sources,
  )

crengine_lib = static_library('crengine',
  cpp_args: debug_flags + crengine_flags,
  dependencies: crengine_dependencies,
  include_directories: [crengine_includes, antiword_includes, chmlib_includes],
  sources: crengine_sources,
  )

crengine_dep = declare_dependency(
  compile_args: crengine_flags,
  link_with: [
    crengine_lib,
    antiword_lib,
    chmlib_lib,
    ],
  include_directories: crengine_includes,
  dependencies: crengine_dependencies,
  )

data_files = ['../cr3.css']

foreach _data: [
  'chm.css',
  'dict.css',
  'doc.css',
  'epub.css',
  'fb2.css',
  'htm.css',
  'html5.css',
  'NOTES.txt',
  'rtf.css',
  'txt.css',
  ]
  data_files += 'cr3gui/data' / _data
endforeach

install_data(data_files,
  install_dir: 'data',
  install_tag: 'runtime',
  )

install_subdir('cr3gui/data/hyph',
  install_dir: 'data',
  install_tag: 'runtime',
  )
