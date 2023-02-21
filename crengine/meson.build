crengine_flags = [
  '-DALLOW_KERNING=1',
  '-DCHM_SUPPORT_ENABLED=1',
  '-DCR3_ANTIWORD_PATCH=1',
  '-DCR_EMULATE_GETTEXT=1',
  '-DENABLE_ANTIWORD=1',
  '-DMATHML_SUPPORT=1',
  '-DUSE_FONTCONFIG=0',
  '-DUSE_FREETYPE=1',
  '-DUSE_FRIBIDI=1',
  '-DUSE_HARFBUZZ=1',
  '-DUSE_LIBUNIBREAK=1',
  '-DUSE_LIBWEBP=1',
  '-DUSE_LUNASVG=1',
  '-DUSE_NANOSVG=0', # better SVG support via LunaSVG
  '-DUSE_SRELL_REGEX=1',
  '-DUSE_UTF8PROC=1',
  '-DUSE_ZSTD=1',
]

if 8 == meson.get_compiler('cpp').sizeof('off64_t',
  args: '-D_LARGEFILE64_SOURCE=1',
  prefix: '#include<<sys/types.h>',
  )
  crengine_flags += ['-D_LARGEFILE64_SOURCE=1', '-DHAVE_STAT64=1']
endif

if host_machine.system() == 'linux'
  crengine_flags += [
    '-DLINUX', 
    '-D_LINUX=1',
    ]
elif host_machine.system() == 'windows'
endif

crengine_includes = include_directories('include')

crengine_sources = files(
  'qimagescale/qimagescale.cpp',
  'src/chmfmt.cpp',
  'src/cp_stats.cpp',
  'src/crconcurrent.cpp',
  'src/cri18n.cpp',
  'src/crskin.cpp',
  'src/crtest.cpp',
  'src/crtxtenc.cpp',
  'src/docxfmt.cpp',
  'src/epubfmt.cpp',
  'src/fb3fmt.cpp',
  'src/hist.cpp',
  'src/hyphman.cpp',
  'src/lstridmap.cpp',
  'src/lvbmpbuf.cpp',
  'src/lvdocview.cpp',
  'src/lvdrawbuf.cpp',
  'src/lvfnt.cpp',
  'src/lvfntman.cpp',
  'src/lvimg.cpp',
  'src/lvmemman.cpp',
  'src/lvopc.cpp',
  'src/lvpagesplitter.cpp',
  'src/lvrend.cpp',
  'src/lvstream.cpp',
  'src/lvstring.cpp',
  'src/lvstsheet.cpp',
  'src/lvstyles.cpp',
  'src/lvtextfm.cpp',
  'src/lvtinydom.cpp',
  'src/lvxml.cpp',
  'src/mathml.cpp',
  'src/odtfmt.cpp',
  'src/odxutil.cpp',
  'src/pdbfmt.cpp',
  'src/props.cpp',
  'src/rtfimp.cpp',
  'src/textlang.cpp',
  'src/txtselector.cpp',
  'src/wolutil.cpp',
  'src/wordfmt.cpp',
)
