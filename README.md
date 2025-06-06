<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# countFalsy

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Count the number of falsy elements in an ndarray.

<section class="intro">

</section>

<!-- /.intro -->

<section class="installation">

## Installation

```bash
npm install @stdlib/ndarray-base-count-falsy
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var countFalsy = require( '@stdlib/ndarray-base-count-falsy' );
```

#### countFalsy( arrays )

Counts the number of falsy elements in an ndarray.

<!-- eslint-disable max-len -->

```javascript
var Float64Array = require( '@stdlib/array-float64' );

// Create a data buffer:
var xbuf = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 0.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0 ] );

// Define the shape of the input array:
var shape = [ 3, 1, 2 ];

// Define the array strides:
var sx = [ 4, 4, 1 ];

// Define the index offset:
var ox = 0;

// Create the input ndarray-like object:
var x = {
    'dtype': 'float64',
    'data': xbuf,
    'shape': shape,
    'strides': sx,
    'offset': ox,
    'order': 'row-major'
};

// Perform operation:
var out = countFalsy( [ x ] );
// returns 1
```

The function accepts the following arguments:

-   **arrays**: array-like object containing an input ndarray.

The provided ndarray should be an `object` with the following properties:

-   **dtype**: data type.
-   **data**: data buffer.
-   **shape**: dimensions.
-   **strides**: stride lengths.
-   **offset**: index offset.
-   **order**: specifies whether an ndarray is row-major (C-style) or column major (Fortran-style).

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   For very high-dimensional ndarrays which are non-contiguous, one should consider copying the underlying data to contiguous memory before performing the operation in order to achieve better performance.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var bernoulli = require( '@stdlib/random-array-bernoulli' );
var ndarray2array = require( '@stdlib/ndarray-base-to-array' );
var countFalsy = require( '@stdlib/ndarray-base-count-falsy' );

var x = {
    'dtype': 'generic',
    'data': bernoulli( 10, 0.75, {
        'dtype': 'generic'
    }),
    'shape': [ 5, 2 ],
    'strides': [ 2, 1 ],
    'offset': 0,
    'order': 'row-major'
};
console.log( ndarray2array( x.data, x.shape, x.strides, x.offset, x.order ) );

var out = countFalsy( [ x ] );
console.log( out );
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

Character codes for data types:

<!-- The following is auto-generated. Do not manually edit. See scripts/loops.js. -->

<!-- charcodes -->

-   **x**: `bool` (boolean).
-   **z**: `complex128` (double-precision floating-point complex number).
-   **c**: `complex64` (single-precision floating-point complex number).
-   **f**: `float32` (single-precision floating-point number).
-   **d**: `float64` (double-precision floating-point number).
-   **k**: `int16` (signed 16-bit integer).
-   **i**: `int32` (signed 32-bit integer).
-   **s**: `int8` (signed 8-bit integer).
-   **t**: `uint16` (unsigned 16-bit integer).
-   **u**: `uint32` (unsigned 32-bit integer).
-   **b**: `uint8` (unsigned 8-bit integer).

<!-- ./charcodes -->

Function name suffix naming convention:

```text
stdlib_ndarray_count_falsy_<input_data_type>_<output_data_type>
```

For example,

<!-- run-disable -->

```c
void stdlib_ndarray_count_falsy_d_i(...) {...}
```

is a function which accepts one double-precision floating-point input ndarray and one signed 32-bit integer output ndarray.

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="usage">

### Usage

```c
#include "stdlib/ndarray/base/count_falsy.h"
```

<!-- The following is auto-generated. Do not manually edit. See scripts/*loops.js. -->

<!-- loops -->

#### stdlib_ndarray_count_falsy_b_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_UINT8;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 2, 1 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_b_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_b_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_b_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_UINT8;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 2, 1 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_b_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_b_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_c_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include "stdlib/complex/float32/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_COMPLEX64;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 16, 8 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_c_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_c_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_c_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include "stdlib/complex/float32/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_COMPLEX64;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 16, 8 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_c_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_c_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_d_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_FLOAT64;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 16, 8 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_d_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_d_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_d_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_FLOAT64;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 16, 8 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_d_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_d_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_f_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_FLOAT32;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 8, 4 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_f_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_f_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_f_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_FLOAT32;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 8, 4 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_f_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_f_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_i_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_INT32;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 8, 4 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_i_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_i_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_i_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_INT32;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 8, 4 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_i_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_i_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_k_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_INT16;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 4, 2 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_k_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_k_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_k_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_INT16;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 4, 2 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_k_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_k_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_s_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_INT8;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 2, 1 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_s_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_s_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_s_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_INT8;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 2, 1 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_s_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_s_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_t_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_UINT16;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 4, 2 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_t_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_t_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_t_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_UINT16;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 4, 2 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_t_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_t_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_u_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_UINT32;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 8, 4 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_u_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_u_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_u_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_UINT32;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 8, 4 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_u_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_u_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_x_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_BOOL;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 2, 1 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_x_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_x_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_x_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_BOOL;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 2, 1 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_x_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_x_l( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_z_i( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include "stdlib/complex/float64/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_COMPLEX128;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 32, 16 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_z_i( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_z_i( struct ndarray *arrays[], void *data );
```

#### stdlib_ndarray_count_falsy_z_l( \*arrays\[], \*data )

Counts the number of falsy elements in an input ndarray.

```c
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include "stdlib/complex/float64/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

// Define the ndarray data types:
enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_COMPLEX128;
enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT64;

// Create underlying byte arrays:
uint8_t xbuf[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
uint8_t ybuf[] = { 0, 0, 0, 0, 0, 0, 0, 0 };

// Define the number of dimensions:
int64_t ndims = 2;

// Define the array shapes:
int64_t shx[] = { 2, 2 };
int64_t *shy = NULL;

// Define the strides:
int64_t sx[] = { 32, 16 };
int64_t sy[] = { 0 };

// Define the index offsets:
int64_t ox = 0;
int64_t oy = 0;

// Define the array order:
enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

// Specify the index mode:
enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

// Specify the subscript index modes:
int8_t submodes[] = { imode };
int64_t nsubmodes = 1;

// Create an input ndarray:
struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
if ( x == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an output ndarray:
struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
if ( y == NULL ) {
    fprintf( stderr, "Error allocating memory.\n" );
    exit( EXIT_FAILURE );
}

// Create an array containing the ndarrays:
struct ndarray *arrays[] = { x, y };

// Perform operation:
int8_t status = stdlib_ndarray_count_falsy_z_l( arrays, NULL );
if ( status != 0 ) {
    fprintf( stderr, "Error during computation.\n" );
    exit( EXIT_FAILURE );
}

// ...

// Free allocated memory:
stdlib_ndarray_free( x );
stdlib_ndarray_free( y );
```

The function accepts the following arguments:

-   **arrays**: `[inout] struct ndarray**` array whose first element is a pointer to an input ndarray and whose second element is a pointer to a zero-dimensional output ndarray.
-   **data**: `[in] void*` function data. This argument is unused and should be a `NULL` pointer.

```c
int8_t stdlib_ndarray_count_falsy_z_l( struct ndarray *arrays[], void *data );
```

<!-- ./loops -->

<!-- macros -->

<!-- TODO: consider documenting macros -->

<!-- ./macros -->

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

* * *

<section class="examples">

### Examples

```c
#include "stdlib/ndarray/base/count_falsy.h"
#include "stdlib/ndarray/dtypes.h"
#include "stdlib/ndarray/index_modes.h"
#include "stdlib/ndarray/orders.h"
#include "stdlib/ndarray/ctor.h"
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>
#include <inttypes.h>

static void print_ndarray_contents( const struct ndarray *x ) {
    int64_t i;
    int32_t v;
    int8_t s;

    for ( i = 0; i < stdlib_ndarray_length( x ); i++ ) {
        s = stdlib_ndarray_iget_int32( x, i, &v );
        if ( s != 0 ) {
            fprintf( stderr, "Unable to resolve data element.\n" );
            exit( EXIT_FAILURE );
        }
        fprintf( stdout, "data[%"PRId64"] = %d\n", i, v );
    }
}

int main( void ) {
    // Define the ndarray data types:
    enum STDLIB_NDARRAY_DTYPE xdtype = STDLIB_NDARRAY_UINT8;
    enum STDLIB_NDARRAY_DTYPE ydtype = STDLIB_NDARRAY_INT32;

    // Create underlying byte arrays:
    uint8_t xbuf[] = { 1, 2, 3, 4, 5, 6, 7, 8 };
    uint8_t ybuf[] = { 0, 0, 0, 0 };

    // Define the number of input array dimensions:
    int64_t ndims = 3;

    // Define the array shapes:
    int64_t shx[] = { 2, 2, 2 };
    int64_t *shy = NULL;

    // Define the strides:
    int64_t sx[] = { 4, 2, 1 };
    int64_t sy[] = { 0 };

    // Define the offsets:
    int64_t ox = 0;
    int64_t oy = 0;

    // Define the array order:
    enum STDLIB_NDARRAY_ORDER order = STDLIB_NDARRAY_ROW_MAJOR;

    // Specify the index mode:
    enum STDLIB_NDARRAY_INDEX_MODE imode = STDLIB_NDARRAY_INDEX_ERROR;

    // Specify the subscript index modes:
    int8_t submodes[] = { imode };
    int64_t nsubmodes = 1;

    // Create an input ndarray:
    struct ndarray *x = stdlib_ndarray_allocate( xdtype, xbuf, ndims, shx, sx, ox, order, imode, nsubmodes, submodes );
    if ( x == NULL ) {
        fprintf( stderr, "Error allocating memory.\n" );
        exit( EXIT_FAILURE );
    }

    // Create an output ndarray:
    struct ndarray *y = stdlib_ndarray_allocate( ydtype, ybuf, 0, shy, sy, oy, order, imode, nsubmodes, submodes );
    if ( y == NULL ) {
        fprintf( stderr, "Error allocating memory.\n" );
        exit( EXIT_FAILURE );
    }

    // Define an array containing the ndarrays:
    struct ndarray *arrays[] = { x, y };

    // Perform operation:
    int8_t status = stdlib_ndarray_count_falsy_b_i( arrays );
    if ( status != 0 ) {
        fprintf( stderr, "Error during computation.\n" );
        exit( EXIT_FAILURE );
    }

    // Print the results:
    print_ndarray_contents( y );
    fprintf( stdout, "\n" );

    // Free allocated memory:
    stdlib_ndarray_free( x );
    stdlib_ndarray_free( y );
}
```

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-base-count-falsy.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-base-count-falsy

[test-image]: https://github.com/stdlib-js/ndarray-base-count-falsy/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ndarray-base-count-falsy/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-base-count-falsy/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-base-count-falsy?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-base-count-falsy.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-base-count-falsy/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ndarray-base-count-falsy/tree/deno
[deno-readme]: https://github.com/stdlib-js/ndarray-base-count-falsy/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ndarray-base-count-falsy/tree/umd
[umd-readme]: https://github.com/stdlib-js/ndarray-base-count-falsy/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ndarray-base-count-falsy/tree/esm
[esm-readme]: https://github.com/stdlib-js/ndarray-base-count-falsy/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ndarray-base-count-falsy/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-base-count-falsy/main/LICENSE

<!-- <related-links> -->

<!-- </related-links> -->

</section>

<!-- /.links -->
