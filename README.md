This is a very simple wrapper around libsodium masquerading as nacl.

[![Build Status](https://travis-ci.org/stef/pysodium.svg?branch=master)](https://travis-ci.org/stef/pysodium)

This wrapper requires a pre-installed libsodium from:

   https://github.com/jedisct1/libsodium

then it provides access to the following functions:

```
crypto_aead_chacha20poly1305_decrypt(ciphertext, ad, nonce, key)
crypto_aead_chacha20poly1305_decrypt_detached(ciphertext, mac, ad, nonce, key)
crypto_aead_chacha20poly1305_encrypt_detached(message, ad, nonce, key)
crypto_aead_chacha20poly1305_encrypt(message, ad, nonce, key)
crypto_aead_chacha20poly1305_ietf_decrypt(ciphertext, ad, nonce, key)
crypto_aead_chacha20poly1305_ietf_encrypt(message, ad, nonce, key)
crypto_auth(message, key)
crypto_auth(tag, message, key)
crypto_auth_verify(h, m, k=b'')
crypto_box_afternm(msg, nonce, k)
crypto_box_beforenm(pk, sk)
crypto_box_detached(msg, nonce, pk, sk)
crypto_box_keypair()
crypto_box(msg, nonce, pk, sk)
crypto_box_open_afternm(c, nonce, k)
crypto_box_open(c, nonce, pk, sk)
crypto_box_open_detached(c, mac, nonce, pk, sk)
crypto_box_seal(msg, pk)
crypto_box_seal_open(c, pk, sk)
crypto_box_seed_keypair(seed)
crypto_generichash_blake2b_salt_personal(message, outlen = crypto_generichash_blake2b_BYTES, key = b'', salt = b'', personal = b'')
crypto_generichash_final(state, outlen=crypto_generichash_BYTES)
crypto_generichash_init(outlen=crypto_generichash_BYTES, k=b'')
crypto_generichash(m, k=b'', outlen=crypto_generichash_BYTES)
crypto_generichash_update(state, m)
crypto_hash_sha256(message)
crypto_hash_sha512(message)
crypto_pwhash(outlen, passwd, salt, opslimit, memlimit, alg)
crypto_pwhash_scryptsalsa208sha256(outlen, passwd, salt, opslimit, memlimit)
crypto_pwhash_scryptsalsa208sha256_str(passwd, opslimit, memlimit)
crypto_pwhash_scryptsalsa208sha256_str_verify(stored, passwd)
crypto_pwhash_str(passwd, opslimit, memlimit)
crypto_pwhash_str_verify(pstr, passwd)
crypto_scalarmult_curve25519_base(n)
crypto_scalarmult_curve25519(n, p)
crypto_secretbox(msg, nonce, k)
crypto_secretbox_open(c, nonce, k)
crypto_sign_init()
crypto_sign_update(state, m)
crypto_sign_final_create(state, sk)
crypto_sign_final_verify(state, sig, pk)
crypto_sign_detached(m, sk)
crypto_sign_keypair()
crypto_sign(m, sk)
crypto_sign_open(sm, pk)
crypto_sign_pk_to_box_pk(pk)
crypto_sign_seed_keypair(seed)
crypto_sign_sk_to_box_sk(sk)
crypto_sign_sk_to_pk(sk)
crypto_sign_sk_to_seed(sk)
crypto_sign_verify_detached(sig, msg, pk)
crypto_stream_chacha20_xor(message, nonce, key)
crypto_stream(cnt, nonce=None, key=None)
crypto_stream_xor(msg, cnt, nonce=None, key=None)
randombytes(size)
```

Constants:

```
crypto_aead_chacha20poly1305_ABYTES
crypto_aead_chacha20poly1305_KEYBYTES
crypto_aead_chacha20poly1305_NONCEBYTES
crypto_aead_chacha20poly1305_ietf_KEYBYTES
crypto_aead_chacha20poly1305_ietf_NONCEBYTES
crypto_auth_BYTES
crypto_auth_KEYBYTES
crypto_box_BOXZEROBYTES
crypto_box_MACBYTES
crypto_box_NONCEBYTES
crypto_box_PUBLICKEYBYTES
crypto_box_SEALBYTES
crypto_box_SECRETKEYBYTES
crypto_box_SEEDBYTES
crypto_box_ZEROBYTES
crypto_generichash_BYTES
crypto_generichash_blake2b_BYTES
crypto_generichash_blake2b_BYTES_MAX
crypto_generichash_blake2b_BYTES_MIN
crypto_generichash_blake2b_KEYBYTES_MAX
crypto_generichash_blake2b_PERSONALBYTES
crypto_generichash_blake2b_SALTBYTES
crypto_hash_sha256_BYTES
crypto_hash_sha512_BYTES
crypto_pwhash_ALG_DEFAULT
crypto_pwhash_MEMLIMIT_INTERACTIVE
crypto_pwhash_MEMLIMIT_MODERATE
crypto_pwhash_MEMLIMIT_SENSITIVE
crypto_pwhash_OPSLIMIT_INTERACTIVE
crypto_pwhash_OPSLIMIT_MODERATE
crypto_pwhash_OPSLIMIT_SENSITIVE
crypto_pwhash_SALTBYTES
crypto_pwhash_STRBYTES
crypto_pwhash_scryptsalsa208sha256_MEMLIMIT_INTERACTIVE
crypto_pwhash_scryptsalsa208sha256_MEMLIMIT_SENSITIVE
crypto_pwhash_scryptsalsa208sha256_OPSLIMIT_INTERACTIVE
crypto_pwhash_scryptsalsa208sha256_OPSLIMIT_SENSITIVE
crypto_pwhash_scryptsalsa208sha256_SALTBYTES
crypto_pwhash_scryptsalsa208sha256_STRBYTES
crypto_pwhash_scryptsalsa208sha256_STRPREFIX
crypto_scalarmult_BYTES
crypto_scalarmult_curve25519_BYTES
crypto_secretbox_BOXZEROBYTES
crypto_secretbox_KEYBYTES
crypto_secretbox_KEYBYTES
crypto_secretbox_MACBYTES
crypto_secretbox_NONCEBYTES
crypto_secretbox_ZEROBYTES
crypto_sign_BYTES
crypto_sign_PUBLICKEYBYTES
crypto_sign_SECRETKEYBYTES
crypto_sign_SEEDBYTES
crypto_sign_ed25519_PUBLICKEYBYTES
crypto_sign_ed25519_SECRETKEYBYTES
crypto_stream_KEYBYTES
crypto_stream_NONCEBYTES
```



Note

most of the the `*_easy` functions are not implemented as the "non-easy"
functions provide already the "easy" interface, which hides the placement of
buffers in memory, which makes little sense in python, so this wrapper handles
this.
