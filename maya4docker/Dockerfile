FROM rockylinux:9.3

# See https://help.autodesk.com/view/MAYAUL/2024/ENU/?guid=GUID-D2B5433C-E0D2-421B-9BD8-24FED217FD7F for the list of packages to install
# RUN yum update -y
# RUN dnf install -y libnsl
RUN dnf install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm && \
    dnf install -y epel-release && \
    dnf install -y \
    audiofile-devel \
    compat-openssl11 \
    dbus \
    e2fsprogs-libs \
    flite \
    fontconfig \
    freetype \
    glibc \
    libcap \
    libdrm \
    liberation-fonts-common \
    liberation-mono-fonts \
    liberation-sans-fonts \
    liberation-serif-fonts \
    libICE \
    libmng \
    libnsl \
    libpng15 \
    libSM \
    libX11 \
    libXau \
    libxcb \
    libXcomposite \
    libxcrypt-compat \
    libXcursor \
    libXdamage \
    libXext \
    libXfixes \
    libXi \
    libXinerama \
    libxkbcommon \
    libxkbcommon-x11 \
    libXmu \
    libXp \
    libXpm \
    libXrandr \
    libXrender \
    libXScrnSaver \
    libxshmfence \
    libXt \
    libXtst \
    mesa-libGLU \
    mesa-libGLw \
    nss \
    openssl-libs \
    pciutils-libs \
    qt5 \
    speech-dispatcher \
    xcb-util \
    xcb-util-image \
    xcb-util-keysyms \
    xcb-util-renderutil \
    xcb-util-wm \
    xorg-x11-fonts-ISO8859-1-100dpi \
    xorg-x11-fonts-ISO8859-1-75dpi \
    zlib \
    && \
    dnf clean all && rm -rf /var/cache/dnf

# See https://help.autodesk.com/view/MAYAUL/2024/ENU/?guid=GUID-E7E054E1-0E32-4B3C-88F9-BF820EB45BE5
COPY Autodesk_Maya_2024_2_Update_Linux_64bit /install
WORKDIR /install/Packages

# For Licencing
RUN yum install -y adskflexnetclient-11.18.0-0.x86_64.rpm \
    adlmapps29-29.0.2-0.x86_64.rpm \
    adsklicensing13.3.1.9694-0-0.x86_64.rpm \
    adskflexnetserverIPV6-11.18.0-0.x86_64.rpm

# Maya
RUN yum install -y Maya2024_64-2024.2-1191.x86_64.rpm

# Create no-root user
RUN adduser user

WORKDIR /home/user
COPY maya4docker/start_licensing_service.sh start_licensing_service.sh
RUN chmod +x start_licensing_service.sh
ENV LD_LIBRARY_PATH=/opt/Autodesk/AdskLicensing/13.3.1.9694/AdskLicensingAgent/lib
