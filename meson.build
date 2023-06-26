project('plugin', ['cpp', 'c'], version : '0.1', default_options : ['buildtype=debug'])

compiler = meson.get_compiler('cpp')

libdir = meson.source_root() / '3p/sdk/lib/public'

tier0 = compiler.find_library('tier0', dirs : libdir)
tier1 = compiler.find_library('tier1', dirs : libdir)
tier2 = compiler.find_library('tier2', dirs : libdir)
tier3 = compiler.find_library('tier3', dirs : libdir)
mathlib = compiler.find_library('mathlib', dirs : libdir)
vstdlib = compiler.find_library('vstdlib', dirs : libdir)
legacy_stdio_definitions = compiler.find_library('legacy_stdio_definitions')

incdirs = include_directories(
  '3p/sdk/public',
  '3p/sdk/public/tier0',
  '3p/sdk/public/tier1',
  )

subdir('src')

plugin = shared_library('plugin', plugin_sources,
  install : true,
  include_directories: incdirs,
  link_args : ['/NODEFAULTLIB:LIBCMT'],
  dependencies : [tier0, tier1, tier2, tier3, mathlib, vstdlib, legacy_stdio_definitions],
  )
