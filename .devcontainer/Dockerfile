FROM frappe/bench:latest

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    zsh \
    git \
    curl \
    fonts-powerline \
    netcat-openbsd \
    mariadb-client && \
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended && \
    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k && \
    sed -i 's/ZSH_THEME=".*"/ZSH_THEME="powerlevel10k\/powerlevel10k"/g' ~/.zshrc && \
    chsh -s $(which zsh) && \
    cp -r /root/.oh-my-zsh /home/frappe/.oh-my-zsh && \
    cp /root/.zshrc /home/frappe/.zshrc && \
    chown -R frappe:frappe /home/frappe/.oh-my-zsh /home/frappe/.zshrc && \
    rm -rf /var/lib/apt/lists/*

USER frappe

SHELL ["/usr/bin/zsh", "-c"]
