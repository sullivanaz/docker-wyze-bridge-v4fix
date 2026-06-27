# 🚀 Docker Wyze Bridge - v4 Camera Fix Edition

[![Docker](https://img.shields.io/badge/Docker-Ready-blue?style=for-the-badge&logo=docker)](https://hub.docker.com/)
[![WebRTC](https://img.shields.io/badge/WebRTC-Enabled-green?style=for-the-badge)](https://webrtc.org/)
[![Wyze v4](https://img.shields.io/badge/Wyze%20v4-Fixed-brightgreen?style=for-the-badge)](https://github.com/nickdnj/docker-wyze-bridge-v4fix)

## 🎯 **THE ULTIMATE SOLUTION FOR WYZE CAM v4 STREAMING**

**🔥 BREAKING:** Wyze Cam v4 cameras stopped working in February 2025? **WE FIXED IT!** 

This repository contains the **definitive solution** for the Wyze Cam v4 connectivity crisis that affected thousands of users worldwide. When Wyze's firmware update broke TUTK protocol support, we didn't just complain - **we built a better solution**.

---

## 🏆 **Why This Fix is AWESOME**

### ⚡ **Instant Problem Solver**
- **v4 cameras working again** within minutes of deployment
- **Zero configuration** required - automatic detection and fallback
- **Backwards compatible** - all your old cameras still work perfectly

### 🧠 **Intelligent Dual-Protocol System**
```
🎥 Legacy Cameras (v1/v2/v3/Pan) → RTSP Streaming (Local, Fast)
🎥 v4 Cameras (HL_CAM4) → WebRTC Streaming (Cloud, Reliable)
```

### 🌟 **Enterprise-Grade Features**
- **Smart camera detection** - automatically identifies v4 vs legacy models
- **Seamless protocol switching** - no manual configuration needed  
- **Production ready** - includes monitoring, logging, and error handling
- **Integration guides** - comprehensive documentation for developers

---

## 🚨 **The Problem We Solved**

**February 2025 Firmware Disaster:**
- ❌ Wyze Cam v4 cameras suddenly stopped streaming
- ❌ TUTK protocol connections timing out  
- ❌ Thousands of users left with broken setups
- ❌ No official fix from Wyze for weeks

**Our Investigation Revealed:**
- Wyze moved v4 cameras to **cloud-only WebRTC streaming**
- TUTK protocol was **permanently disabled** for HL_CAM4 models
- Legacy cameras remained unaffected
- **Solution required dual-protocol architecture**

---

## 🚀 **Quick Start - Get Your v4 Cameras Working NOW**

### 1️⃣ **Clone This Repo**
```bash
git clone https://github.com/nickdnj/docker-wyze-bridge-v4fix.git
cd docker-wyze-bridge-v4fix
```

### 2️⃣ **Setup Your Credentials**
```bash
# Create .env file with your Wyze credentials
WYZE_EMAIL=your-email@example.com
WYZE_PASSWORD=your-password
API_ID=your-api-id
API_KEY=your-api-key
```

### 3️⃣ **Deploy the Fix**
```bash
# Use the standard bridge (cameras visible, v4 via WebRTC)
docker-compose up -d

# OR use production config
docker-compose -f docker-compose.prod.yml up -d
```

### Published Docker Image

This fork publishes a multi-architecture image to GitHub Container Registry:

```text
ghcr.io/sullivanaz/docker-wyze-bridge-v4fix:latest
```

Version tags are also published from Git tags, for example:

```text
ghcr.io/sullivanaz/docker-wyze-bridge-v4fix:1.2.3
```

Example `docker-compose.yml`:

```yaml
services:
  wyze-bridge:
    image: ghcr.io/sullivanaz/docker-wyze-bridge-v4fix:latest
    container_name: wyze-bridge-v4fix
    restart: unless-stopped
    ports:
      - 1935:1935 # RTMP
      - 8554:8554 # RTSP
      - 8888:8888 # HLS
      - 8889:8889 # WebRTC
      - 8189:8189/udp # WebRTC/ICE
      - 5000:5000 # Web UI
    environment:
      - WYZE_EMAIL=${WYZE_EMAIL}
      - WYZE_PASSWORD=${WYZE_PASSWORD}
      - API_ID=${API_ID}
      - API_KEY=${API_KEY}
      - WB_AUTH=true
    volumes:
      - ./config:/config
      - ./media:/media
```

### 4️⃣ **Celebrate! 🎉**
- **All cameras visible** at: `http://localhost:5000`
- **v4 cameras streaming** via WebRTC endpoints
- **Legacy cameras** continue via RTSP as always

---

## 🎮 **Access Your Fixed v4 Cameras**

### 🌐 **WebRTC Endpoints (v4 Cameras)**
```
📺 Direct WebRTC Player: http://localhost:5000/webrtc/YOUR_CAMERA_NAME
🔗 Signaling Endpoint: http://localhost:5000/signaling/YOUR_CAMERA_NAME?kvs
📊 Camera Status: http://localhost:5000/api/sse_status
```

### 📡 **RTSP Streams (Legacy Cameras)**  
```
📹 RTSP Stream: rtsp://localhost:8554/YOUR_CAMERA_NAME
🎬 HLS Stream: http://localhost:8888/YOUR_CAMERA_NAME/stream.m3u8
```

---

## 🏗️ **Integration with Other Projects**

### 🎯 **Perfect for VistterStudio Integration**

We've included **comprehensive integration guides** for developers:

- **[📋 Integration Guide](INTEGRATION_GUIDE.md)** - Complete technical documentation
- **[⚡ Quick Reference](V4_CAMERA_ENDPOINTS.md)** - Specific endpoints and examples  
- **[📚 Changelog](WYZE_V4_FIX_CHANGELOG.md)** - Detailed technical explanation

### 🔧 **Developer-Friendly**
```javascript
// Example: Automatic protocol detection
async function getStreamEndpoint(cameraName) {
    const camera = await getCameraInfo(cameraName);
    
    return camera.model === "HL_CAM4" 
        ? { type: 'webrtc', url: `http://localhost:5000/webrtc/${cameraName}` }
        : { type: 'rtsp', url: `rtsp://localhost:8554/${cameraName}` };
}
```

---

## 🎖️ **Technical Achievements**

### 🧪 **What We Discovered**
- **Root cause analysis** of the February 2025 firmware update
- **Protocol reverse engineering** to understand WebRTC requirements
- **AWS KVS integration** for cloud streaming
- **Dual-protocol architecture** design and implementation

### 🛠️ **What We Built**
- **Smart camera detection** system
- **Automatic protocol fallback** mechanisms  
- **WebRTC signaling** integration with AWS
- **Production deployment** configurations
- **Comprehensive monitoring** and logging

---

## 🤝 **Contributing**

Found this fix helpful? **Star this repo!** ⭐

Want to improve it further? **PRs welcome!** 

---

## 📞 **Support & Community**

### 🆘 **Need Help?**
- **[📖 Integration Guide](INTEGRATION_GUIDE.md)** - Comprehensive documentation
- **[⚡ Quick Reference](V4_CAMERA_ENDPOINTS.md)** - Fast answers
- **[🐛 Issues](https://github.com/nickdnj/docker-wyze-bridge-v4fix/issues)** - Report problems

---

## 🏆 **Credits & Acknowledgments**

### 🙏 **Built Upon Giants**
- **[mrlt8/docker-wyze-bridge](https://github.com/mrlt8/docker-wyze-bridge)** - Original excellent foundation
- **Wyze Community** - Problem identification and testing

### 💡 **Innovation Credits**
- **Dual-protocol architecture** - Our original design
- **Smart camera detection** - Automatic model identification  
- **WebRTC integration** - AWS KVS cloud streaming

---

## 🎯 **TL;DR - The Bottom Line**

**🔥 Wyze Cam v4 broken? WE FIXED IT!**

1. **Clone this repo** 
2. **Add your credentials**
3. **Run docker-compose**
4. **Enjoy working v4 cameras!**

**⚡ It's literally that simple.**

---

<div align="center">

### ⭐ **If this saved your setup, give us a star!** ⭐

**[🚀 Get Started Now](https://github.com/nickdnj/docker-wyze-bridge-v4fix)**

</div>

---

*Made with ❤️ by developers who refuse to accept "it's broken" as a final answer.*
