FROM httpd:alpine
RUN apk add --no-cache openssh
COPY docker-entrypoint.sh /
COPY wrapper.sh /
RUN rm -rf /etc/ssh/ssh_host_rsa_key /etc/ssh/ssh_host_dsa_key
EXPOSE 22
RUN ["chmod", "+x", "/*.sh"]
ENTRYPOINT ["/docker-entrypoint.sh"]
RUN sed -i s/\#PermitRootLogin\ prohibit-password/PermitRootLogin\ yes/g /etc/ssh/sshd_config
CMD ["/wrapper.sh"]