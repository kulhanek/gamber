# ==============================================================================
# GAmber CMake File
# ==============================================================================

INSTALL(FILES
            gamber
        DESTINATION
            bin
        PERMISSIONS
            OWNER_EXECUTE GROUP_EXECUTE WORLD_EXECUTE OWNER_READ GROUP_READ WORLD_READ
        )

