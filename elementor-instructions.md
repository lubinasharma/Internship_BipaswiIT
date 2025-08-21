# How to Add Thumbnail Slider to Elementor

## Copy-Paste Ready Code for Elementor

Here's the complete code to copy and paste into Elementor's HTML widget:

```html
<!-- Thumbnail Slider Widget - Copy everything from here -->
<div class="thumbnail-slider-container">
    <!-- Main Image Display -->
    <div class="main-image-container">
        <img id="mainImage" src="https://picsum.photos/800/500?random=1" alt="Main Image" class="main-image">
        <div class="image-overlay">
            <div class="image-counter">
                <span id="currentImageNumber">1</span> / 4
            </div>
        </div>
        <!-- Navigation Arrows -->
        <button class="nav-arrow prev-arrow" onclick="changeImage(-1)">❮</button>
        <button class="nav-arrow next-arrow" onclick="changeImage(1)">❯</button>
    </div>

    <!-- Thumbnail Navigation -->
    <div class="thumbnail-container">
        <div class="thumbnail-wrapper">
            <img src="https://picsum.photos/800/500?random=1" alt="Thumbnail 1" class="thumbnail active" onclick="showImage(0)">
            <img src="https://picsum.photos/800/500?random=2" alt="Thumbnail 2" class="thumbnail" onclick="showImage(1)">
            <img src="https://picsum.photos/800/500?random=3" alt="Thumbnail 3" class="thumbnail" onclick="showImage(2)">
            <img src="https://picsum.photos/800/500?random=4" alt="Thumbnail 4" class="thumbnail" onclick="showImage(3)">
        </div>
    </div>
</div>

<style>
.thumbnail-slider-container {
    max-width: 800px;
    margin: 0 auto;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    overflow: hidden;
}

.main-image-container {
    position: relative;
    width: 100%;
    height: 500px;
    overflow: hidden;
    background: #f8f9fa;
}

.main-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: all 0.4s ease;
    cursor: pointer;
}

.main-image:hover {
    transform: scale(1.02);
}

.image-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(to bottom, rgba(0,0,0,0.3) 0%, transparent 30%, transparent 70%, rgba(0,0,0,0.3) 100%);
    opacity: 0;
    transition: opacity 0.3s ease;
    pointer-events: none;
}

.main-image-container:hover .image-overlay {
    opacity: 1;
}

.image-counter {
    position: absolute;
    top: 20px;
    right: 20px;
    background: rgba(0, 0, 0, 0.7);
    color: white;
    padding: 8px 16px;
    border-radius: 20px;
    font-size: 14px;
    font-weight: 500;
}

.nav-arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(255, 255, 255, 0.9);
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    font-size: 18px;
    cursor: pointer;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
    opacity: 0;
}

.main-image-container:hover .nav-arrow {
    opacity: 1;
}

.prev-arrow {
    left: 20px;
}

.next-arrow {
    right: 20px;
}

.nav-arrow:hover {
    background: white;
    transform: translateY(-50%) scale(1.1);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

.thumbnail-container {
    padding: 20px;
    background: #f8f9fa;
}

.thumbnail-wrapper {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
}

.thumbnail {
    width: 120px;
    height: 80px;
    object-fit: cover;
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.3s ease;
    border: 3px solid transparent;
    opacity: 0.7;
}

.thumbnail:hover {
    opacity: 1;
    transform: translateY(-2px);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.thumbnail.active {
    border-color: #007cba;
    opacity: 1;
    transform: translateY(-2px);
    box-shadow: 0 4px 15px rgba(0, 124, 186, 0.3);
}

/* Responsive Design */
@media (max-width: 768px) {
    .thumbnail-slider-container {
        margin: 0 10px;
    }
    
    .main-image-container {
        height: 300px;
    }
    
    .thumbnail {
        width: 80px;
        height: 60px;
    }
    
    .thumbnail-wrapper {
        gap: 8px;
    }
    
    .nav-arrow {
        width: 40px;
        height: 40px;
        font-size: 16px;
    }
    
    .prev-arrow {
        left: 10px;
    }
    
    .next-arrow {
        right: 10px;
    }
    
    .image-counter {
        top: 10px;
        right: 10px;
        padding: 6px 12px;
        font-size: 12px;
    }
}

@media (max-width: 480px) {
    .main-image-container {
        height: 250px;
    }
    
    .thumbnail {
        width: 70px;
        height: 50px;
    }
    
    .thumbnail-container {
        padding: 15px;
    }
}
</style>

<script>
// Image data - Replace these URLs with your actual image URLs
const images = [
    {
        main: 'https://picsum.photos/800/500?random=1',
        thumb: 'https://picsum.photos/800/500?random=1',
        alt: 'Beautiful landscape 1'
    },
    {
        main: 'https://picsum.photos/800/500?random=2',
        thumb: 'https://picsum.photos/800/500?random=2',
        alt: 'Beautiful landscape 2'
    },
    {
        main: 'https://picsum.photos/800/500?random=3',
        thumb: 'https://picsum.photos/800/500?random=3',
        alt: 'Beautiful landscape 3'
    },
    {
        main: 'https://picsum.photos/800/500?random=4',
        thumb: 'https://picsum.photos/800/500?random=4',
        alt: 'Beautiful landscape 4'
    }
];

let currentImageIndex = 0;

// Initialize the slider
function initSlider() {
    const mainImage = document.getElementById('mainImage');
    const thumbnails = document.querySelectorAll('.thumbnail');
    
    // Set up images
    images.forEach((img, index) => {
        if (thumbnails[index]) {
            thumbnails[index].src = img.thumb;
            thumbnails[index].alt = img.alt;
        }
    });
    
    // Show first image
    showImage(0);
}

// Show specific image
function showImage(index) {
    if (index < 0 || index >= images.length) return;
    
    currentImageIndex = index;
    const mainImage = document.getElementById('mainImage');
    const thumbnails = document.querySelectorAll('.thumbnail');
    const counter = document.getElementById('currentImageNumber');
    
    // Update main image with fade effect
    mainImage.style.opacity = '0';
    
    setTimeout(() => {
        mainImage.src = images[index].main;
        mainImage.alt = images[index].alt;
        mainImage.style.opacity = '1';
    }, 200);
    
    // Update thumbnails
    thumbnails.forEach((thumb, i) => {
        thumb.classList.toggle('active', i === index);
    });
    
    // Update counter
    counter.textContent = index + 1;
}

// Navigate images with arrows
function changeImage(direction) {
    const newIndex = currentImageIndex + direction;
    
    if (newIndex >= images.length) {
        showImage(0); // Loop to first
    } else if (newIndex < 0) {
        showImage(images.length - 1); // Loop to last
    } else {
        showImage(newIndex);
    }
}

// Keyboard navigation
document.addEventListener('keydown', function(e) {
    if (e.key === 'ArrowLeft') {
        changeImage(-1);
    } else if (e.key === 'ArrowRight') {
        changeImage(1);
    }
});

// Auto-play functionality (optional - uncomment to enable)
/*
let autoPlayInterval;

function startAutoPlay() {
    autoPlayInterval = setInterval(() => {
        changeImage(1);
    }, 4000); // Change image every 4 seconds
}

function stopAutoPlay() {
    clearInterval(autoPlayInterval);
}

// Start autoplay on load
document.addEventListener('DOMContentLoaded', function() {
    startAutoPlay();
    
    // Pause autoplay on hover
    const container = document.querySelector('.thumbnail-slider-container');
    container.addEventListener('mouseenter', stopAutoPlay);
    container.addEventListener('mouseleave', startAutoPlay);
});
*/

// Initialize when DOM is loaded
document.addEventListener('DOMContentLoaded', initSlider);

// Also initialize immediately in case DOM is already loaded
if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', initSlider);
} else {
    initSlider();
}
</script>
<!-- End of Thumbnail Slider Widget -->
```

## How to Use in Elementor:

### Step 1: Add HTML Widget
1. Edit your page with Elementor
2. Drag and drop the **HTML** widget to your desired location
3. Click on the HTML widget to open its settings

### Step 2: Paste the Code
1. Copy the entire code above (from `<!-- Thumbnail Slider Widget -->` to `<!-- End of Thumbnail Slider Widget -->`)
2. Paste it into the HTML widget's code area
3. Click "Update" to save

### Step 3: Customize Your Images
Replace the placeholder image URLs in the JavaScript section with your own images:

```javascript
const images = [
    {
        main: 'YOUR_IMAGE_1_URL_HERE',
        thumb: 'YOUR_THUMBNAIL_1_URL_HERE', 
        alt: 'Description of image 1'
    },
    // ... repeat for all 4 images
];
```

## Features Included:

✅ **Responsive Design** - Works on all devices  
✅ **Touch/Click Navigation** - Click thumbnails to navigate  
✅ **Arrow Navigation** - Left/right arrows on hover  
✅ **Keyboard Support** - Use arrow keys to navigate  
✅ **Smooth Transitions** - Fade effects between images  
✅ **Image Counter** - Shows current image number  
✅ **Modern Styling** - Clean, professional appearance  
✅ **Auto-play Option** - Uncomment code to enable  

## Customization Options:

### Change Colors:
- Modify `border-color: #007cba;` for active thumbnail border
- Change `background: rgba(0, 0, 0, 0.7);` for counter background

### Adjust Sizes:
- Change `.main-image-container height: 500px;` for main image height
- Modify thumbnail dimensions: `width: 120px; height: 80px;`

### Enable Auto-play:
Uncomment the auto-play section in the JavaScript to enable automatic image rotation.

## Browser Compatibility:
- Chrome, Firefox, Safari, Edge
- Internet Explorer 11+
- Mobile browsers (iOS Safari, Chrome Mobile)