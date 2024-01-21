:title: Old Note
:category: Crypto

Old Note
========


Challenge Description
---------------------

**50 Points**

The worn parchment bears the mark of a distinguished leader, its edges frayed
with time. Ink, faded yet legible, recounts the grand vision of a ruler,
detailing conquests and strategies etched in a language of diplomacy and
authority.

.. image:: img/old_note.jpg

Overview
--------

The image shows what appears to be the flag in cipher text (evedent by the two
curly braces). Some of the ciphertext appears to be illegible so it may require
more than just determining the cipher.

My best read of the ciphertext is ``yxqqbiib{bvb(3?)4jb_bvbpxt_(f?)(3?)0knr3oba}``
(``(?)`` indicates the illegible characters).

Identifying the cipher
----------------------
Let's focus on the first part of the ciphertext (``yxqqbiib``). Since it is
known that the flag prefix for the competition is ``battelle`` and observed
that the repeated letters in the cipher text are also repeated in the flag
prefix, some kind of subsitution cipher is a good first guess. The challenge
description also references the "grand vision of a ruler, detailing conquests
and strategies etched in a language of diplomacy and authority". Given that
info a "caesar shift cipher" seems to be the best starting point.

Caesar shift ciphers
--------------------

The caesar shift cipher is a type of subsitution cipher which shifts the
alphabet with wraparound and subsitutes the plaintext character for the
character in the shifted alaphabet.

These subsitution ciphers are vulnerable to a plaintext attack, where knowing
some of the plaintext in a cipher can reveal the key.

::
    
    Shift       3 3 3 3 3 3 3 3
    ciphertext  y x q q b i i b
    plaintext   b a t t e l l e

The flag prefix "battelle" appears when shifting the alphabet by 3. Let's use
this shift to decode rest of the ciphertext. Note that characters not part of
the alphabet are not shifted (such as number and symbols).

::

    ciphertext  yxqqbiib{bvb34jb_bvbpxt_f30knr3oba}
    plaintext   battelle{eye34me_eyesaw_i30nqu3red}

The decoded flag was **not** correct, which indicates some of our letter
guesses were wrong. The flag appears to be a leet-speak variation of
"eyecame_eyesaw_iconqucred". The letter "C" is encoded by the letter "Z" in the
ciphertext, which looks similar to the number 3 when drawn in calligraphy. Let's
try swapping the letter out and decoding again:

::

    ciphertext  yxqqbiib{bvbz4jb_bvbpxt_fz0knrzoba}
    plaintext   battelle{eyec4me_eyesaw_ic0nqucred}

That was still **incorrect** so looking at the photo again, the last z/3 looks
very clearly like a 3. Swapping that character back to a 3 gives us the correct
flag.

::

    ciphertext  yxqqbiib{bvbz4jb_bvbpxt_fz0knr3oba}
    plaintext   battelle{eyec4me_eyesaw_ic0nqu3red}
