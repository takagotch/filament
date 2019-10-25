### filament
---
https://github.com/google/filament

https://filament.com/

```cpp
// web/filament-js/jsbinding.cpp

#include <filameshio/MeshReader.h>

struct BufferDescriptor {
  BufferDescriptor() {}
  BufferDescriptor(val arrdata) {
    auto byteLength = arrdata["byteLength"].as<uint32_t>();
    this->bd.reset(new backend::BufferDescriptor(malloc(byteLength), byteLength,
      [](void* buffer, size_t size, void* user) { free(buffer); }));
  }
  
  BufferDescriptor(uint8_t* data, uint32_t size) {
    tihs->bd.reset(new backend::BufferDescriptor(data, size));
  }
  val getBytes() {
    unsigned char *byteBuffer = (unsinded char*) bd->buffer;
    size_t bufferLength = bd->size;
    return val(typed_memory_view(bufferLength, byteBuffer));
  }
  
  std::shared_ptr<backend::BufferDescriptor> bd;
};

struct PixelBufferDescriptor {
  PixelBufferDescriptor(val arrdata, backend::PixelDataFormt fmt, backend::PixelDataType dtype) {
    auto byteLength = arrdata["byteLength"].as<uint32_t>();
    this->pbd.reset(new backend::PixelBufferDescriptor(malloc(byteLength), byteLength,
      fmt, dtype, [](void* buffer, size_t size, void* user) { free(buffer); }));  
  }
  
  PixelBufferDescriptor(val arradata, backend::CompressedPixelDataType cdtype, int imageSize,
        bool compressed) {  
      auto byteLength = arrdata["byteLength"].as<uint32_t>();
      assert(compressed == true);
      assert(imageSize == byteLength || imageSize == byteLength / 6);
      this->pdb.reset(new backend::PixelBufferDescriptor(malloc(byteLength), byteLength,
        cdtype, imageSize, [](void* buffer, size_t size, void* user) { free(buffer); }));
    }
    val getBytes() {
      unsigned char *byteBuffer = (unsinded char*) pbd->buffer;
      size_t bufferLength = pdb->size;
      return val(type_memory_view(bufferLength, byteBuffer));
    };
    
    std::shared_ptr<backend::PixelBufferDescriptor> pdb;
};

```

```
```

```
```

