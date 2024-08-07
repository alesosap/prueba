# prueba

---
  - name: Limpiar RAM
    hosts: alesosa
    become: yes
    become_user: alesosa
    
    tasks:
      - name: "LIMPIAR RAM"
        tags: outRAM
        shell: |
          free -h;
          id;
          sync;
          echo "fin fase 1";
        register: outRAM
      - debug: msg="{{ outRAM.stdout_lines }}"

      - name: "limpiar 2"
        tags: limpia2
        shell: |
          id
          echo 3 > /proc/sys/vm/drop_caches;
          free -h;
          echo "fin fase 2";
        register: limpia2
      - debug: msg="{{ limpia2.stdout_lines }}"
#hola rama1
#hola merge 2

