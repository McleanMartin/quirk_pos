pkgdatadir = join_paths(get_option('prefix'), get_option('datadir'), meson.project_name())
moduledir = join_paths(pkgdatadir, 'quirk')
gnome = import('gnome')

gnome.compile_resources('quirk',
  'quirk.gresource.xml',
  gresource_bundle: true,
  install: true,
  install_dir: pkgdatadir,
)

python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', join_paths(get_option('prefix'), get_option('localedir')))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
  input: 'quirk.in',
  output: 'quirk',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir')
)

quirk_sources = [
  '__init__.py',
  'main.py',
  'screens/splash.py',
]

install_data(quirk_sources, install_dir: moduledir)
