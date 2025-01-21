# Copyright (c) 2025, Postgres Professional

# Does not support the PGXS infrastructure at this time. Please, compile as part
# of the contrib source tree.

pg_tsparser_sources = files(
  'tsparser.c'
)

if host_system == 'windows'
  pg_tsparser_sources += rc_lib_gen.process(win32ver_rc, extra_args: [
    '--NAME', 'pg_tsparser',
    '--FILEDESC', 'pg_tsparser - modifies the default text parsing strategy.',])
endif

pg_tsparser = shared_module('pg_tsparser',
  pg_tsparser_sources,
  kwargs: contrib_mod_args,
)
contrib_targets += pg_tsparser

install_data(
  'pg_tsparser.control',
  'pg_tsparser--1.0.sql',
  kwargs: contrib_data_args,
)

tests += {
  'name': 'pg_tsparser',
  'sd': meson.current_source_dir(),
  'bd': meson.current_build_dir(),
  'regress': {
    'sql': [
      'pg_tsparser',
    ],
  },
}
