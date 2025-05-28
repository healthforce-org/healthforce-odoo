FROM odoo:18.0

USER root
RUN apt-get update && apt-get install -y --no-install-recommends \
    nano \
    curl \
    git \
 && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN pip3 install --no-cache-dir --break-system-packages debugpy

RUN mkdir -p /mnt/extra-addons && chown -R odoo:odoo /mnt/extra-addons

USER odoo

COPY --chown=odoo:odoo ./odoo_addons /mnt/extra-addons

CMD ["odoo", "-c", "/etc/odoo/odoo.conf"]
