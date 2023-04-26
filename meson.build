project('bimg', 'cpp')

bimg = library(
	'bimg',
	[
		'src/image_cubemap_filter.cpp',
		'src/image_decode.cpp',
		'src/image_encode.cpp',
		'src/image_gnf.cpp',
		'src/image.cpp'
	],
	include_directories: include_directories('include')
)

bimg_dep = declare_dependency(
	include_directories: include_directories('include'),
	link_with: bimg
)
