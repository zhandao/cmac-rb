##cmac-rb

This gem implements the CMAC keyed hash function as described in [RFC 4493](http://tools.ietf.org/html/rfc4493). The CMAC function is written as a low-level C extension on top of OpenSSL, for speed and compatibility.

AES-CMAC provides stronger assurance of data integrity than a checksum or an error-detecting code.  The verification of a checksum or an error-detecting code detects only accidental modifications of the data, while CMAC is designed to detect intentional, unauthorized modifications of the data, as well as accidental modifications.
 
AES-CMAC achieves a security goal similar to that of HMAC. Since AES-CMAC is based on a symmetric key block cipher, AES, and HMAC is based on a hash function, such as SHA-1, AES-CMAC is appropriate for information systems in which AES is more readily available than a hash function.

###Install

    gem 'cmac-rb'

###Usage

```ruby
    example = ['2b7e151628aed2a6abf7158809cf4f3c', '', 'bb1d6929e95937287fa37d129b756746']
    key, plaintext, expected_cmac = example.map { |x| [x].pack('H*') }
    
    # you can also pass a 16 bit key, instead of calling .pack()
    digest = CMAC::Digest.new(key)
    tag = digest.update(plaintext)
      
    expect(tag).to eq expected_cmac
```

###Reference

- [RFC 4493](http://tools.ietf.org/rfc/rfc4493.txt) - The AES-CMAC algorithm
- [NIST SP 800-38B](http://csrc.nist.gov/publications/nistpubs/800-38B/SP_800-38B.pdf) - The CMAC Mode for Authentication 

###License

This program is released under the GNU Affero General Public License.
