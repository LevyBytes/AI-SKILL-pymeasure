# Upcoming release - Deprecated

- The behavior that silently returns str from `values` and property creators such as `control` when casting fails is now deprecated. Use an explicit helper, for example `cast_or_str(float)`, for that case.

- Toptica Ibeamsmart `enable_continous` is deprecated; replace it with `enable_continuous`.

- Thermotron 3800 `initalize_oven` is deprecated; use `initialize_oven` instead.
