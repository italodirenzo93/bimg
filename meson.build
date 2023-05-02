project('bimg', ['c', 'cpp'])

is_debug = get_option('debug')
if is_debug
	add_project_arguments('-DBX_CONFIG_DEBUG=1', language: 'cpp')
else
	add_project_arguments('-DBX_CONFIG_DEBUG=0', language: 'cpp')
endif

bx_dep = dependency('bx')

bimg = static_library(
	'bimg',
	[
		'src/image_gnf.cpp',
		'src/image.cpp',

		# miniz
		'3rdparty/tinyexr/deps/miniz/miniz.c',

		# astc-encoder
		'3rdparty/astc-encoder/source/astcenc_averages_and_directions.cpp',
		'3rdparty/astc-encoder/source/astcenc_block_sizes.cpp',
		'3rdparty/astc-encoder/source/astcenc_color_quantize.cpp',
		'3rdparty/astc-encoder/source/astcenc_color_unquantize.cpp',
		'3rdparty/astc-encoder/source/astcenc_compress_symbolic.cpp',
		'3rdparty/astc-encoder/source/astcenc_compute_variance.cpp',
		'3rdparty/astc-encoder/source/astcenc_decompress_symbolic.cpp',
		'3rdparty/astc-encoder/source/astcenc_diagnostic_trace.cpp',
		'3rdparty/astc-encoder/source/astcenc_entry.cpp',
		'3rdparty/astc-encoder/source/astcenc_find_best_partitioning.cpp',
		'3rdparty/astc-encoder/source/astcenc_ideal_endpoints_and_weights.cpp',
		'3rdparty/astc-encoder/source/astcenc_image.cpp',
		'3rdparty/astc-encoder/source/astcenc_integer_sequence.cpp',
		'3rdparty/astc-encoder/source/astcenc_mathlib.cpp',
		'3rdparty/astc-encoder/source/astcenc_mathlib_softfloat.cpp',
		'3rdparty/astc-encoder/source/astcenc_partition_tables.cpp',
		'3rdparty/astc-encoder/source/astcenc_percentile_tables.cpp',
		'3rdparty/astc-encoder/source/astcenc_pick_best_endpoint_format.cpp',
		'3rdparty/astc-encoder/source/astcenc_quantization.cpp',
		'3rdparty/astc-encoder/source/astcenc_symbolic_physical.cpp',
		'3rdparty/astc-encoder/source/astcenc_weight_align.cpp',
		'3rdparty/astc-encoder/source/astcenc_weight_quant_xfer_tables.cpp'
	],
	include_directories: include_directories([
		'include',
		'3rdparty/astc-encoder/include',
		'3rdparty/tinyexr/deps/miniz'
	]),
	dependencies: [
		bx_dep
	]
)

bimg_decode = static_library(
	'bimg_decode',
	[
		'src/image_decode.cpp'
	],
	include_directories: include_directories([
		'include',
		'3rdparty',
		'3rdparty/tinyexr/deps/miniz'
	]),
	dependencies: [
		bx_dep
	]
)

bimg_encode = static_library(
	'bimg_encode',
	[
		'src/image_encode.cpp',
		'src/image_cubemap_filter.cpp',

		# libsquish
		'3rdparty/libsquish/alpha.cpp',
		'3rdparty/libsquish/clusterfit.cpp',
		'3rdparty/libsquish/colourblock.cpp',
		'3rdparty/libsquish/colourfit.cpp',
		'3rdparty/libsquish/colourset.cpp',
		'3rdparty/libsquish/maths.cpp',
		'3rdparty/libsquish/rangefit.cpp',
		'3rdparty/libsquish/singlecolourfit.cpp',
		'3rdparty/libsquish/squish.cpp',

		# edtaa3
		'3rdparty/edtaa3/edtaa3func.cpp',

		# etc1
		'3rdparty/etc1/etc1.cpp',

		# etc2
		'3rdparty/etc2/ProcessRGB.cpp',
		'3rdparty/etc2/Tables.cpp',

		# nvtt
		'3rdparty/nvtt/nvtt.cpp',
		'3rdparty/nvtt/bc6h/zoh_utils.cpp',
		'3rdparty/nvtt/bc6h/zoh.cpp',
		'3rdparty/nvtt/bc6h/zohone.cpp',
		'3rdparty/nvtt/bc6h/zohtwo.cpp',
		'3rdparty/nvtt/bc7/avpcl_mode0.cpp',
		'3rdparty/nvtt/bc7/avpcl_mode1.cpp',
		'3rdparty/nvtt/bc7/avpcl_mode2.cpp',
		'3rdparty/nvtt/bc7/avpcl_mode3.cpp',
		'3rdparty/nvtt/bc7/avpcl_mode4.cpp',
		'3rdparty/nvtt/bc7/avpcl_mode5.cpp',
		'3rdparty/nvtt/bc7/avpcl_mode6.cpp',
		'3rdparty/nvtt/bc7/avpcl_mode7.cpp',
		'3rdparty/nvtt/bc7/avpcl_utils.cpp',
		'3rdparty/nvtt/bc7/avpcl.cpp',
		'3rdparty/nvtt/nvmath/fitting.cpp',

		# pvrtc
		'3rdparty/pvrtc/BitScale.cpp',
		'3rdparty/pvrtc/MortonTable.cpp',
		'3rdparty/pvrtc/PvrTcDecoder.cpp',
		'3rdparty/pvrtc/PvrTcEncoder.cpp',
		'3rdparty/pvrtc/PvrTcPacket.cpp',

		# iqa
		'3rdparty/iqa/source/convolve.c',
		'3rdparty/iqa/source/decimate.c',
		'3rdparty/iqa/source/math_utils.c',
		'3rdparty/iqa/source/ms_ssim.c',
		'3rdparty/iqa/source/mse.c',
		'3rdparty/iqa/source/psnr.c',
		'3rdparty/iqa/source/ssim.c'
	],
	include_directories: include_directories([
		'include',
		'3rdparty',
		'3rdparty/astc-encoder/include',
		'3rdparty/iqa/include',
		'3rdparty/nvtt',
		'3rdparty/tinyexr/deps/miniz'
	]),
	dependencies: [
		bx_dep
	]
)

bimg_dep = declare_dependency(
	include_directories: include_directories('include'),
	link_with: [
		bimg,
		bimg_decode,
		bimg_encode
	]
)
