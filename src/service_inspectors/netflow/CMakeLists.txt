
set ( NETFLOW_INCLUDES
    netflow_record.h
)

set ( FILE_LIST
    ${NETFLOW_INCLUDES}
    netflow_cache.h
    netflow_headers.h
    netflow_module.cc
    netflow_module.h
    netflow.cc
    netflow.h
)

if (STATIC_INSPECTORS)
    add_library( netflow OBJECT ${FILE_LIST})

else (STATIC_INSPECTORS)
    add_dynamic_module(netflow inspectors ${FILE_LIST})

endif (STATIC_INSPECTORS)

install(FILES ${NETFLOW_INCLUDES}
    DESTINATION "${INCLUDE_INSTALL_PATH}/service_inspectors/netflow"
)
