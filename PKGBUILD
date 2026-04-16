# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2022, 2023, 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
#   Konstantin Gizdov
#     <arch at kge dot pw>
#   Caleb Maclennan
#     <caleb@alerque.com>
# Contributors:
#   Baptiste Jonglez
#     <archlinux at bitsofnetworks dot org>

if [[ ! -v "_os" ]]; then
  _os="$(
    uname \
      -o)"
fi
if [[ "${_os}" == "Android" ]]; then
  _libc="ndk-sysroot"
  _compiler="clang"
  _libcompiler="libllvm"
  _sh="dash"
elif [[ "${_os}" == "GNU/Linux" ]]; then
  _libc="glibc"
  _compiler="gcc"
  _libcompiler="libgcc"
  _sh="sh"
elif [[ "${_os}" == "Msys" ]]; then
  _libc="msys2-w32api-runtime"
  _libc_headers="msys2-w32api-headers"
  _compiler="gcc"
  _libcompiler="gcc-libs"
  _sh="sh"
else
  _msg=(
    "Unknown os '${_os}'."
  )
  msg \
    "${_msg[*]}"
  _libc="msys2-w32api-runtime"
  _libc_headers="msys2-w32api-headers"
  _compiler="gcc"
  _libcompiler="gcc-libs"
  _sh="sh"
fi
_evmfs_available="$(
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_transfig" ]]; then
  # See https://sourceforge.net/p/mcj/discussion/general/thread/4bae083308
  _transfig="false"
fi
if [[ ! -v "_tag_name" ]]; then
  _tag_name="pkgver"
fi
if [[ ! -v "_archive_format" ]]; then
  _archive_format="tar.xz"
  if [[ "${_tag_name}" == "pkgver" ]]; then
    _archive_format="tar.xz"
  fi
fi
_pkg=fig2dev
pkgbase="${_pkg}"
pkgname=(
  "${pkgbase}"
)
_pkgver="3.2.9a"
pkgver="3.2.9.1"
pkgrel=6
pkgdesc="Format conversion utility that can be used with xfig"
arch=(
  'aarch64'
  'arm'
  'armv7l'
  'armv8l'
  'i686'
  'mips'
  'pentium4'
  'powerpc'
  'x86_64'
)
url="http://mcj.sourceforge.net/"
license=(
  "Xfig"
)
depends=(
  'bash'
  'bc'
  'ghostscript'
  "${_libc}"
  'libpng'
  'libxpm'
  'netpbm'
  'zlib'
)
makedepends=(
  # "automake"
  "autoconf"
  "coreutils"
  "${_compiler}"
)
if [[ "${_os}" == "Msys" ]]; then
  makedepends+=(
  )
fi
if [[ "${_transfig}" == "true" ]]; then
  conflicts=(
    'transfig'
  )
  replaces=(
    'transfig'
  )
  provides=(
    'transfig'
  )
fi
if [[ "${_tag_name}" == "pkgver" ]]; then
  _tag="${_pkgver}"
fi
_tarname="${_pkg}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
_3_2_9_sum='15e246c8d13cc72de25e08314038ad50ce7d2defa9cf1afc172fd7f5932090b1'
_sum="61e185393176852f03b901b3b05b19fbc5ad8258ff142f3da6e70b1b83513326"
_sig_sum="bdf8bb3460e9150a9ca0449f729052b279a3abfccfa53f61ad838fe48da7d876"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  _src="${_evmfs_src}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  _uri="https://downloads.sourceforge.net/mcj/${_tarfile}"
  _src="${_tarfile}::${_uri}"
fi
source+=(
  "${_src}"
  # "${_pkg}-3.2.9-remove_broken_tests.patch"
)
sha256sums=(
  "${_sum}"
  # '32e1fe1d99c76db7d49cb46245442cdf0fce693c3ebcde7b47913ebafb0c72fa'
)
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

prepare() {
  # remove broken tests:
  # https://sourceforge.net/p/mcj/tickets/171/
  # patch \
  #   -Np1 \
  #   -d \
  #     "${_tarname}" \
  #   -i \
  #   "../${_tarname}-remove_broken_tests.patch"
  # delete pre-generated test script
  rm \
    -v \
    "${_tarname}/${_pkg}/tests/testsuite"
  # extract license file from sources
  sed \
    -n \
    '1,17p' \
    "${_tarname}/${_pkg}/alloc.h" > \
    "Xfig.txt"
  cd \
    "${_tarname}"
  autoreconf \
    -fiv
}

build() {
  local \
    _configure_opts=()
  _configure_opts+=(
    --prefix="/usr"
  )
  if [[ "${_transfig}" == "true" ]]; then
    _configure_opts+=(
      --enable-transfig
    )
  fi
  cd \
    "${_tarname}"
  "./configure" \
    "${_configure_opts[@]}"
  make
}

check() {
  cd \
    "${_tarname}"
  make \
    check
}

package() {
  cd \
    "${_tarname}"
  make \
    DESTDIR="${pkgdir}" \
    XFIGLIBDIR="/usr/share/xfig" \
    FIG2DEV_LIBDIR="/usr/share/${_pkg}" \
    MANPATH="/usr/share/man" \
    install
  install \
    -vDm644 \
    "../Xfig.txt" \
    -t \
    "${pkgdir}/usr/share/licenses/${_pkg}/"
}
